<script>
  export let question;
  export let update_score;
  let isDisabled = false;
  let actualAnswer;
  let wrongAnswers = question.incorrect_answers.map((answer) => {
    return { answer, correct: false };
  });

  let unshuffledAnswers = [
    ...wrongAnswers,
    { answer: question.correct_answer, correct: true },
  ];
  console.log("all", unshuffledAnswers);

  let isCorrect;
  let questionAnswered = false;

  function shuffle(arr) {
    let current = arr.length,
      tempValue,
      randomIndex;
    while (0 !== current) {
      randomIndex = Math.floor(Math.random() * current);
      current -= 1;

      tempValue = arr[current];
      arr[current] = arr[randomIndex];
      arr[randomIndex] = tempValue;
    }
    return arr;
  }
  let options = shuffle(unshuffledAnswers);

  function checkAnswer(correct, allOptions) {
    console.log("check answer");
    questionAnswered = true;
    isCorrect = correct;
    update_score(isCorrect);
    isDisabled = true;
    actualAnswer = allOptions.find(option => option.correct).answer;
  }

</script>

<container>
<h2>
  {@html question.question}
</h2>
{#if questionAnswered}
  <h3>
    {@html isCorrect ? "Well done!" : `Wrong, the correct answer is ${actualAnswer}`}
  </h3>
{/if}

<div class='buttons'>
{#each options as option}
  <button
    on:click={() => {
      checkAnswer(option.correct, options);
    }}
    disabled={isDisabled}
  >
    {@html option.answer}
  </button>
{/each}
</div>

</container>

<style>
  container{
    padding: 25px 5px;
    margin: 25px auto;
    border-radius: 5px;
    border-width: 2px;
    border-style: solid;
    border-color: #71a7b7;
    display: grid;
    flex-direction: column;
    max-width: 800px;
    align-content: center;
  }

  .buttons{
    display: grid;
    grid-template-columns: 1fr 1fr;
  }
  button {
    border: none;
    margin: 10px;
    border-radius: 10px;
    background-color:#71a7b7;
    cursor: pointer;

  }
  button:hover {
    border: none;
    opacity: 80%;
    color: white;
    transition: .2s;
  } 

  button:disabled {
    opacity: unset;
    background-color: rgb(201, 201, 201);
    color: rgb(134, 134, 134);
    cursor:default;
  }




  h2, h3 {
    text-align: center;
  }
</style>
