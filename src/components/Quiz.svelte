<script>

import { onMount } from 'svelte';

    import Questions from './Questions.svelte';
    import Score from './Score.svelte';

	const APIURL = 'https://opentdb.com/api.php?amount=10&category=11&difficulty=easy&type=multiple';


	export let quiz;
    quiz = getData();
     let response;
	
        // onMount(async () => {
		// const res = await fetch(APIURL);
		// response = await res.json();
		// response = response.results;
		// console.log('response', response);
		// return response;
        // });

    async function getData() {
    const response = await fetch(APIURL); 
    let fullData = await response.json();
	console.log('data----->', fullData.results)
    quiz = fullData.results;
	return quiz;
}

export function handleClick() {
    return getData();

}
</script>

<div>
    <p>This is from Quiz.svelte</p>
    <div>
        <h2> Select difficulty level</h2>
    <button>Easy</button>
    <button>Medium</button>
    <button>Hard</button>

</div>
    {#await quiz}
    ...Loading 
    {:then res}
    {#each res as question}
    <Questions {question} />
    {/each}
    {/await}
    <!-- <button on:click={handleClick}>History</button> -->

</div>
