<script>
	let userInput = ''
	let activeQ = 0
  let questions = [{hint1:'Sophie has half as many apples as Sally.' , hint2:'Sarah has three times as many apples as Sohpie.', hint3: 'Sally has twice as many apples as Sarah.', query: 'How many apples does Sally have?', correct: '6',}]

		function checkAnswers() {
			
			
	if (userInput == questions[0].correct) {
			
			console.log('correct')

		} else {
			console.log('incorrect')
		}
	}
	function getRandom() {
  	let number = Math.floor(Math.random() * 11);
		return number
	}
</script>



{#each questions as {hint1, hint2, hint3, userInput, query, correct}}

  <p>{hint1}</p>
  <p>{hint2}</p>
  <p>{hint3}</p>
  <p>{query}</p>

{/each}

  <label>
    <input bind:value={userInput}>
  </label>
  <br><br>

  <button on:click={checkAnswers}>Submit</button>


