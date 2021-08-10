<script>
  let questions = [{questionId: 1 , hint1:'' , hint2:'', hint3: ''},]

function getRandom() {
  let number = Math.floor(Math.random() * 11);
return number


}






</script>

{#each questions as {questionId, hint1, hint2, hint3}}

<p>{questions.hint1}</p>
{/each}