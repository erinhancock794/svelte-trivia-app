<!-- A # character always indicates a block opening tag. A / character always indicates a block closing tag. A : character, as in {:else}, indicates a block continuation tag.  -->
<!-- use tween to show a progress bar -->

<script>
	import Quiz from './components/Quiz.svelte'
    // import Questions from './components/Questions.svelte'
	// import {onMount} from 'svelte'
// import { log } from 'node:console';

	console.log('quizzzzz', Quiz);
	// let response = [];

	export let name;
	// function getQuiz() {
	// 	return Quiz;
	// }

	// const APIURL = 'https://opentdb.com/api.php?amount=10&category=11&difficulty=easy&type=multiple';

	// let data = getQuiz();
	// onMount(async () => {
	// 	const res = await fetch(APIURL);
	// 	response = await res.json();
	// 	response = response.results;
	// 	console.log('response', response);
	// 	return response;
	// });

// async function getData() {
//     const response = await fetch(APIURL); 
//     let fullData = await response.json();
// 	console.log('data----->', fullData)
// 	return fullData;
// }

// function handleClick() {
// 	return data;
// }
</script>

<h2>Movie {name} Quiz</h2>

<Quiz />

	<!-- <button on:click={getQuiz()}>Start</button> -->

<!-- <div class='quiz'>
    {#each response as question}
	<Questions {question} />

    {/each} -->


    <!-- {#await data}
    ...Loading 
    {:then trivia}
    {#each trivia.results as question}
    <Questions {question} />
    {/each}
    {/await} -->
    <!-- <button on:click={handleClick}>History</button> -->

<!-- </div> -->






<!-- to deploy: npm run build -->