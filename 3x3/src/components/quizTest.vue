<template>

<form action="javascript:" v-on:submit="validate()">
<div v-for="(item, index) in quiz" :key="item.id" >
    {{index+1}}. {{item[0][0]}}<br>
			
	<input type="radio" :name="index" :id="item[1][0]" :value="item[1][0]" v-model="answer" />
	<label :for="item[1]">{{item[1][0]}}</label>

	<input type="radio" :name="index" :id="item[1][1]" :value="item[1][1]" v-model="answer" />
	<label :for="item[1]">{{item[1][1]}}</label>
			<input type="submit" value="Lock In Answer" :id="index"/> {{submitted[index]}}
    </div>
		</form>
        <button @click="check">Check/Reset</button>
        <audio id="audio" src="https://interactive-examples.mdn.mozilla.net/media/cc0-audio/t-rex-roar.mp3"></audio>
        <div class="fail" v-if="reloader"><button @click="reload">Try Again</button></div>
        
</template>



<script>
export default {
data() {
		return {
            reloader: false,
            answer: "",
            submitted: [],
            correct: ["a","c","w","z"],
            quiz: 
            [
                [["What is the first letter of the alphabet?"],["a", "b"]],
                [["What is the third letter of the alphabet?"],["c", "d"]],
                [["What is the fourth to last letter of the alphabet?"],["w", "x"]],
                [["What is the last letter of the alphabet?"],["y", "z"]] 
            ],
			
		}
	},
	methods: {
		validate() {
            if(this.answer){
            this.submitted.push(this.answer)
            }
            this.answer = null
            console.log()
		},
        play() {
        var audio = document.getElementById("audio");
        audio.play();
        },
        check(){
            this.reloader = true;
            let a = Object.values(this.correct).toString() 
            let b = Object.values(this.submitted).toString() 
            if(a === b){
                this.play()
                setTimeout(this.reload, 2500)

            }
        },
        reload(){
            window.location.reload();
        }
	},
}
</script>

<style>

</style>