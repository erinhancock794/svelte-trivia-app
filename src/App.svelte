<!-- A # character always indicates a block opening tag. A / character always indicates a block closing tag. A : character, as in {:else}, indicates a block continuation tag.  -->
<!-- use tween to show a progress bar -->

<script>
	import Quiz from './components/Quiz.svelte'

	export let name; //main.js
</script>

<h2>Movie {name} Quiz</h2>
<p></p>

<Quiz />







<!-- to deploy: npm run build -->