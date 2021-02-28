<!-- A # character always indicates a block opening tag. A / character always indicates a block closing tag. A : character, as in {:else}, indicates a block continuation tag.  -->
<!-- use tween to show a progress bar -->

<script>
	import Quiz from './components/Quiz.svelte'

	export let name; //main.js
</script>

<h2>{name} Quiz</h2>
<p></p>

<Quiz />


<style>
	h2{
		text-align: center;
		font-size: 3em;
	}
</style>




<!-- to deploy: npm run build -->