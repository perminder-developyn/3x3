```
<template>
  <div class="grid-component">
    <form v-on:submit="validate()">
      <div v-for="(question, index) in quiz" :key="question">
        {{ question.question }}<br />
        <div v-for="(answer, i) in question.answers" :key="answer[i]">
        <input
          type="radio"
          :name="index"
          :value="answer"
          :key="i"
          v-model="submitted[index]"
        />
        <label>{{answer}}</label>
        </div>

      </div>
    </form>
    <button @click="check">Check</button>
    <audio
      id="audio"
      src="https://interactive-examples.mdn.mozilla.net/media/cc0-audio/t-rex-roar.mp3"
    ></audio>
    <div class="fail" v-if="reloader">
      <button @click="reload">Try Again</button>
    </div>
  </div>
</template>



<script>
export default {
  data() {
    return {
      reloader: false,
      answer: "",
      submitted: [],
      correct: ["a", "c", "w", "z"],
      quiz: [
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
      ],
    };
  },
  methods: {
    play() {
      const audio = document.getElementById("audio");
      audio.play();
    },
    check() {
      let a = Object.values(this.correct).toString();
      let b = Object.values(this.submitted).toString();
      console.log(this.submitted, this.correct)
      // changing this to this.correct === this.submitted returns false ???
      if (a === b) {
        this.play();
        setTimeout(this.reload, 2500);
      }else{
          this.reloader = true;
      }
    },
    reload() {
      window.location.reload();
    },
  },
};
</script>

<style>
</style>