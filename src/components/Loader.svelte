<script>
    import Questions from "./Questions.svelte";
    export let selectedCategory;
    export let selectedDifficulty;
    let correctScore = 0;
    let incorrectScore = 0;
        
    const difficulties = {
        EASY: 'easy',
        MEDIUM: 'medium',
        HARD: 'hard'
    }

    function getUrl(difficultySetting, category) {
        const difficulty = difficulties[difficultySetting];

        return `https://opentdb.com/api.php?amount=10&category=${category}&difficulty=${difficulty}&type=multiple`;
    }

    async function getData(attempts = 0) {
        const url = getUrl(selectedDifficulty, selectedCategory);
        const response = await fetch(url);
        let fullData = await response.json();
        if (fullData.response_code === 0) {
            return fullData.results;
        } else if (fullData.response_code === 1) {
            throw new Error(
                "Sorry, we don't have enough questions with that category and difficulty. Please select a new category and difficulty and try agian."
            );
        } else if (attempts < 3) {
            return getData(attempts + 1);
        } else {
            throw new Error(
                "Our questions provider is not currently working, please try again."
            );
        }
    }

    function updateScore(isCorrect) {
        if (isCorrect) {
            correctScore += 1;
        } else {
            incorrectScore += 1;
        }
    }

    let quiz = getData();
</script>

<style>
    p {
        color: #012345;
    }

    #correct span{
        color: green;
    }

    #wrong span{
        color: red;
    }
</style>

<div>
    <div class="score">
    <h2>Score</h2>
    <p id="correct">Correct: <span> {correctScore}</span></p>
    <p id="wrong">Wrong: <span>{incorrectScore}</span></p>
    </div>
    {#await quiz}
        ...Loading
    {:then res}
        {#each res as question}
            <Questions {question} update_score={updateScore} />
        {/each}
    {:catch error}
        <p>{error.message}</p>
    {/await}
</div>
