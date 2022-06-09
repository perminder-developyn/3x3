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
    {#if reloader}
      	<button on:click={reload}>Try Again</button>
    {/if}
    <audio  
		bind:paused={paused}
		id="audio" 
		src="https://interactive-examples.mdn.mozilla.net/media/cc0-audio/t-rex-roar.mp3" >
    </audio>
</div>

<script>
let paused = true;
let reloader = false;
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
    
function submitter(answer, i) {
    submitted[i] = answer
};

function play() {
	paused = !paused
};

function check() {
	let analysis = [];
	correct.forEach((c) => {
		submitted.forEach((s) => {
			if (c === s)
			analysis.push(c === s);
			else {
				reloader = true;
			}
		});
	 });
	 if(analysis.length === 4){
		 play();
		 setTimeout(reload, 2500);
	 };
}

function reload() {
    window.location.reload();
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