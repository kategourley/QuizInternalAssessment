<script>
	let userInput = ''
  let a = 0
  let result = ''
  let score = 0
  let hideNext = true
  let hideSubmit = false
  let hideQuiz = true
  let hideUserInfo = false
  let hideFinish = true
  let name = ''
  let age = ''
  let error = ''

  let questions = [{hint1:'https://cdn.the-scientist.com/assets/articleNo/68759/aImg/42171/tiger-shark-l.jpg' , hint2:'They are one of the largest shark species, growing up to 5.5m and 900kg.', hint3: 'They are named for the distinctive grey stripes/spots littering the sides of their bodies.', query: 'What species of shark is this?', correct: 'tiger',}, {hint1:'https://static.independent.co.uk/s3fs-public/thumbnails/image/2019/03/04/12/mako-shark-.jpg', hint2:'They are the fastest sharks in the world with speeds of 96km/h, which allows them to jump out of the water to heights of up to 9m.', hint3: 'Their favourite meal is swordfish, despite them being such a hard prey to catch.', query: 'What species of shark is this?', correct: 'mako',},]

	function checkAnswers() {
		hideSubmit = true
		if (userInput == questions[a].correct || userInput == [questions[a].correct + ' shark'] || userInput == [questions[a].correct + 'shark'] || userInput == [questions[a].correct + ' sharks']) {
			result = 'correct'
			score += 1
    } else if (userInput == '') {
result = 'Please input a valid answer.'
hideSubmit = false
score += 0
    } else { 
			result = 'incorrect'
			score += 0
		}
if (a == 9) {
  hideQuiz = true
  hideFinish = false
} else {
  if (result == 'incorrect' || result == 'correct') {
      hideNext = false
      } else {
      hideNext = true
    }
}
    

	}
	
	function next() {
			a += 1
		result = ''
		userInput = ''
   hideNext = true
    hideSubmit = false
	}

  function start() {
    if (name == '') {

      error = 'Please enter a valid name.'
    } else if (age == '' || 0 > age || age > 100){
      error = 'Please enter a valid age. Only numbers between 0 and 100 are accepted.'
      } else {
      hideQuiz = false
      hideUserInfo = true
    }

   
   
  }

   function playAgain() {
      hideFinish = true
      hideQuiz = true
      hideUserInfo = false
    }
</script>

<div class:hideQuiz>
<img src={questions[a].hint1} alt='{questions[a].correct}'>
<!-- <p>
	{questions[a].hint1}
</p> -->
<p>
	{questions[a].hint2}
</p>
<p>
	{questions[a].hint3}
</p>
<p>
	{questions[a].query}
</p>
<label>
	<input bind:value={userInput}>
</label>
  
<br><br>

 <button on:click={checkAnswers} class:hideSubmit>Submit</button>
<button on:click={next} class:hideNext>Next</button>
<p>
	{result}
</p>
<p>
	Score = {score}
</p>

</div>
<div class:hideUserInfo>
  <h1>Welcome!</h1>
  <label>Name: 
    <input bind:value={name}>
    </label>
    <label>
      Age: 
      <input type=number min=0 max=10 bind:value={age}>
      </label>
      
    <button on:click={start}>Start</button>
<p>{error}</p>
  </div>
  <div class:hideFinish>
<p> Well done, {name}!</p>
<p>You got {score}/10 correct!</p>
<button on:click={playAgain}>Play Again</button>
    </div>
<style>
  img {
    width: auto;
    height: 200px;
  }

  .hideNext {
    display: none;
  }

  .hideSubmit {
    display: none;
  }

.hideQuiz {
    display: none;
  }

.hideUserInfo {
    display: none;
  }

  .hideFinish {
    display: none;
  }
</style>