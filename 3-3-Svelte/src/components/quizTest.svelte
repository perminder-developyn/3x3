<div class="grid-component">
    {#each quiz as question, index}
      		{question.question}
		<div class="answers">
    		{#each question.answers as answer, i}
				<input 
					type="radio" 
					name={index} 
					on:input={()=>submitter(answer, index, i)} value={answer} key={i} 
				/>
				<label>{answer}</label>
			{/each}           
		</div> 
    {/each}
    
    <button on:click={check}>Check</button>
    {#if incorrect}
      	<h4>Incorrect. Please try again </h4>
    {/if}
	{#if pass}
      	<h4>Congratulations! You passed! </h4>
    {/if}
    <audio  
		bind:paused={paused}
		id="audio" 
		src="https://interactive-examples.mdn.mozilla.net/media/cc0-audio/t-rex-roar.mp3" >
    </audio>
</div>

<script>
let paused = true;
let incorrect = false;
let pass = false;
let submitted = [];
let correct = ['a', 'c', 'w', 'z'];
let quiz = [
		{
			question: 'What is the first letter of the alphabet?',
			answers: ['a', 'b'],
		},
		{
			question: 'What is the third letter of the alphabet?',
			answers: ['c', 'd'],
		},
		{
			question: 'What is the fourth to last letter of the alphabet?',
			answers: ['w', 'x'],
		},
		{
			question: 'What is the last letter of the alphabet?',
			answers: ['y', 'z'],
		},
	];
    
const submitter = (answer, i) => {
    submitted[i] = answer
};

const play = () => {
	paused = !paused
};

const check = () => {
	let analysis = [];
	correct.forEach(c => {
		submitted.forEach(s => {
			if (c === s)
				analysis.push(c === s);
			else 
				incorrect = true;
		});
	});

	if (analysis.length === 4) {
		incorrect = false;
		pass = true;
		play();
	};
}
</script>
  
<style>
.answers {
	display: flex;
}

label {
	padding-right: 1rem;
}

.grid-component {
    padding: 2rem;
}
</style>