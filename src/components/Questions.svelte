
<script>
    export let question;
    //populating DOM with multiple choice options
    let wrongAnswers;
    wrongAnswers = question.incorrect_answers.map((answer) => {
        return {answer, correct: false}
    })

    let unshuffledAnswers = [...wrongAnswers, {answer: question.correct_answer, correct: true}]
    console.log('all', unshuffledAnswers);


    let isCorrect;
    let questionAnswered = false;

    function shuffle(arr){
        let current = arr.length, tempValue, randomIndex;
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

    function checkAnswer(correct){
        console.log('check answer');
        questionAnswered = true;
        isCorrect = correct;
    }

    

  </script>

  
  <h2>
    {@html question.question}
  </h2>
{#if questionAnswered}
  <h3>{isCorrect ? 'Congrats! You\'re not a fucking idiot!' : 'Wow, you are so wrong.'}</h3>

{/if}

  {#each options as option}
  <button on:click={() => {
      checkAnswer(option.correct)
    //   <Score {updateScore}()/>
      }}> 
    {@html option.answer} 
</button>
  {/each}

