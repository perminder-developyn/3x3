<div class="grid-component">
    {#each quiz as question, index}
      <div>
      {question.question}
      </div>
      {#each question.answers as answer, i}
        <div>
          <input type="radio" name={index} on:input={()=>submitter(answer, index, i)} value={answer} key={i} />
          <label> {answer} </label> 
        </div> 
      {/each}           
    {/each}
    
    <button on:click={check}>Check</button>
    <audio  id="audio"
    src="https://interactive-examples.mdn.mozilla.net/media/cc0-audio/t-rex-roar.mp3">
    </audio>
    {#if reloader}
      <div class="fail">
    <button on:click={reload}>Try Again</button>
      </div>
    {/if}
</div>

<script>
let reloader = false;
let submitted = [];
let correct = ["a", "c", "w", "z"];
let quiz = [
           {
            question: "What is the first letter of the alphabet?",
            answers: ["a", "b"],
           },
           {
            question: "What is the third letter of the alphabet?",
            answers: ["c", "d"],
           },
           {
            question: "What is the fourth to last letter of the alphabet?",
            answers: ["w", "x"],
           },
           {
            question: "What is the last letter of the alphabet?",
            answers: ["y", "z"],
           },
           ];
    
function submitter(answer, i) {
    submitted[i] = answer
    }

function play() {
    const audio = document.getElementById("audio");
    audio.play();
    }

function check() {
    let a = Object.values(correct).toString();
    let b = Object.values(submitted).toString();
    // changing this to this.correct === this.submitted returns false ???
    if (a === b) {
      play();
      setTimeout(reload, 2500);
    }else{
      reloader = true;
      }
    }

function reload() {
    window.location.reload();
    }
</script>
  
<style>
    .grid-component {
        flex: 1 1 30%; 
        margin: 5px;
        padding: 2rem; 
    }
</style>