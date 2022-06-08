<template>
	<div class="grid-component">
        <div v-for="(question, index) in quiz" :key="question">
            {{ question.question }}
            <div v-for="(answer, i) in question.answers" :key="answer[i]">
                <input
					type="radio"
					:name="index"
					:value="answer"
					:key="i"
					v-model="submitted[index]"
				/>
				<label>{{ answer }}</label>
			</div>
        </div>
        <button @click="check">Check Answers</button>
        <div class="fail" v-if="reloader">
            <button @click="reload">Try Again</button>
        </div>
		<audio
			ref="audio"
            src="https://interactive-examples.mdn.mozilla.net/media/cc0-audio/t-rex-roar.mp3">
        </audio>
    </div>
</template>


<script>
export default {
    data() {
		return {
			reloader: false,
			answer: '',
			submitted: [],
			correct: ['a', 'c', 'w','z'],
			analysis: [],
			quiz: [
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
			],
		};
	},
	methods: {
		play() {
			this.$refs.audio.play();
		},
		check() {
			this.analysis = []
			this.correct.forEach((c) => {
				this.submitted.forEach((s) => {
					if (c === s)
						this.analysis.push(c === s)
					else {
						this.reloader = true;
					}
				})
			})
			if (this.analysis.length === 4) {
				this.play();
				setTimeout(this.reload, 2500);
			}
		},
		reload() {
			window.location.reload();
		},
	},
};
</script>
