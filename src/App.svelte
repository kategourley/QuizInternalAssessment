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
  let qnNum = a + 1

  let questions = [{hint1:'https://cdn.the-scientist.com/assets/articleNo/68759/aImg/42171/tiger-shark-l.jpg' , hint2:'They are one of the largest shark species, growing up to 5.5m and 900kg.', hint3: 'They are named for the distinctive grey stripes/spots littering the sides of their bodies.', query: 'What species of shark is this?', correct: 'tiger',}, {hint1:'https://static.independent.co.uk/s3fs-public/thumbnails/image/2019/03/04/12/mako-shark-.jpg', hint2:'They are the fastest sharks in the world with speeds of 96km/h, which allows them to jump out of the water to heights of up to 9m.', hint3: 'Their favourite meal is swordfish, despite them being such a hard prey to catch.', query: 'What species of shark is this?', correct: 'mako',}, {hint1:'https://oceana.org/sites/default/files/shutterstock_366230828_0.jpg',hint2: "While the young are in their mother's stomach they swallow their own teeth, which may be to reutilize calcium and minerals.", hint3: 'They are responsible for 5 to 10 attacks per year.', query: 'What species of shark is this?', correct: 'great white'}, {hint1:'https://upload.wikimedia.org/wikipedia/en/thumb/5/55/Lemonshark.JPG/1200px-Lemonshark.JPG', hint2: 'These sharks are named for their yellow-brown skin that helps them camouflage in the sandy, tropical waters they inhabit.', hint3: 'They can be found at depths up to approximately 90m.', query: 'What species of shark is this?', correct: 'lemon'},
  {hint1:'https://static2.stuff.co.nz/1379241118/491/9168491.jpg', hint2: 'This shark is often found resting on the seabed where it’s mottled skin colour blends in perfectly with shells, rocks, and weeds.', hint3: 'They have quite large mouths at the end of their bodies whereas most sharks have their mouths underneath.', query: 'What species of shark is this?', correct: 'carpet'},
{hint1:'https://www.doc.govt.nz/thumbs/hero/contentassets/017b45c72ea84f2d8019ede87d1f37f8/whale-shark-hero.jpg', hint2: 'These sharks can grow up to 12 metres long.', hint3: "It's thought that less than 10% of these sharks survive to adulthood, but those that do may live to 150 years old.", query: 'What species of shark is this?', correct: 'whale'},
{hint1:'https://images2.minutemediacdn.com/image/upload/c_crop,h_2097,w_3732,x_0,y_154/v1554921579/shape/mentalfloss/538474-istock-154125901.jpg?itok=cPzt_mUB', hint2: 'They reach lengths of 3.5m and weights of up to nearly 315kg.', hint3: 'They are known to eat several species of bony fishes and also small sharks, some mammals (both terrestrial and marine), seabirds, and occasionally sea turtles.', query: 'What species of shark is this?', correct: 'bull'},
{hint1:'https://oceana.org/sites/default/files/styles/lightbox_full/public/45_1.jpg?itok=_T4XClF-', hint2: 'This shark gets its name from the cookie-shaped bite wounds it leaves on its prey. The shark’s unique teeth and short, coned snout create these round chunks. It will attach itself to a tuna, marlin, stingray, another shark, or even a whale, by suctioning its lips to the body of the animal. Then, the shark spins its body, using it’s lower set of serrated teeth like a can opener to remove a hunk of flesh, resulting in a wound that lives up to the shark’s name.', hint3: 'These sharks are covered with light organs, likely used for either communication or camouflage.', query: 'What species of shark is this?', correct: 'cookiecutter'},
{hint1:'https://upload.wikimedia.org/wikipedia/commons/0/0b/Cetorhinus_maximus_by_greg_skomal.JPG', hint2: "This shark's common name derives from its habit of feeding at the surface.", hint3: 'Although it has hundreds of small teeth, this shark does not use them when feeding; instead, it usually swims with its mouth open and catches whatever plankton is filtered through.' , query: 'What species of shark is this?', correct: 'basking'},
{hint1:'https://upload.wikimedia.org/wikipedia/commons/thumb/3/3c/Speartooth_shark_melbourne.jpg/1200px-Speartooth_shark_melbourne.jpg', hint2: 'This shark is a rare species of river shark, it inhabits coastal marine waters and tidal reaches of large tropical rivers in northern Australia and New Guinea.', hint3: 'Unlike other species of sharks, this shark uses tidal currents to move in the water. Flooding tides carry these sharks upstream, while ebbing tides return it. Relying on the tidal currents, these sharks can travel 6.2 to 7.5 miles in both directions.', query: 'What species of shark is this?', correct: 'speartooth'}
  
  ]

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
         while (result == 'incorrect') {
         result += '; the correct answer was ' + questions[a].correct + '.'
       }
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
    qnNum = a + 1
	}

  function start() {
    userInput = ''
    a = 0
    result = ''
    score = 0
    hideNext = true
    hideSubmit = false


     if (name == '') {
         error = 'Please enter a valid name.'
     } else if (age == '' || 0 > age || age > 122){
       error = 'Please enter a valid age. Only numbers between 0 and 122 are accepted.'
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
<h2>Question {qnNum}:</h2>
<img src={questions[a].hint1} alt='{questions[a].correct}'>
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
      <input type=number min=0 max=122 bind:value={age}>
      </label>
      
    <button on:click={start}>Start</button>
<p>{error}</p>
  </div>
  <div class:hideFinish>
<p> Well done, {name}! For someone of {age} years of age, you're pretty smart.</p>
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