<script>
    import Loader from "./Loader.svelte";

    let chosenDifficulty;
    let selectedCategory;

    export function handleClick() {
        return getData();
    }

    function pickDifficulty(difficulty) {
        return () => {
            console.log(`The difficulty is ${difficulty}`);
            chosenDifficulty = difficulty;
        };
    }

    function selectCategory(event) {
        console.log(`The category is ${event.target.value}`);
        selectedCategory = event.target.value;
    }
</script>

<div>

    {#if chosenDifficulty && selectedCategory}
        <Loader {selectedCategory} selectedDifficulty={chosenDifficulty} />
    {:else}
    <h2> Select Topic</h2>
        <select bind:value={selectedCategory} on:blur={selectCategory}>
            <option value={9}>General Knowledge</option>
            <option value={10}>Entertainment: Books</option>
            <option value={11}>Entertainment: Film</option>
            <option value={12}>Entertainment: Music</option>
            <option value={16}>Entertainment: Board Games</option>
            <option value={20}>Mythology</option>
            <option value={18}>Science: Computers</option>
        </select>
        <div class="difficulty">
            <h2>Select difficulty level</h2>
            <button on:click={pickDifficulty("EASY")}>Easy</button>
            <button on:click={pickDifficulty("MEDIUM")}>Medium</button>
            <button on:click={pickDifficulty("HARD")}>Hard</button>
        </div>
        <p>Waiting for difficulty and category to be selected...</p>
    {/if}
</div>

<style>
    div{
        /* display: grid; */
        /* flex-direction: column; */
        text-align: center; 

    }
    .difficulty button{
        /* margin: 10px;*/
        border-radius: 10px; 
        padding: 10px;
        margin: 5px;
        background-color:#71a7b7;
        cursor: pointer;
        border: none;
    }
    .difficulty button:hover{
        opacity: 80%;
        color: white;
        transition: .2s;
        border: none;
    }

</style>