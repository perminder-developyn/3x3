<template>
<div class="grid-component">
    <button class="ball" v-on:click="suspense">{{reply}}</button>
</div>
</template>

<script>
export default{
    data(){
        return {
            question:'',
            reply:'8',
            replies: [
                "As I see it, yes",
                "Ask again later",
                "Better not tell you now",
                "Cannot predict now",
                "Concentrate and ask again",
                "Don’t count on it",
                "It is certain",
                "It is decidedly so",
                "Most likely",
                "My reply is no",
                "My sources say no",
                "Outlook good",
                "Outlook not so good",
                "Reply hazy try again",
                "Signs point to yes",
                "Very doubtful",
                "Without a doubt",
                "Yes",
                "Yes, definitely",
                "You may rely on it",         
            ]
        }
    },
    methods:{
        randomReply(){
            this.reply = this.replies[Math.floor(Math.random()*this.replies.length)]
        },
        suspense(){
            this.reply = ""
            setInterval(this.loader, 500)
            setTimeout(this.randomReply, 3000)
            setTimeout(this.reload, 9000)
        },
        loader(){
            if(this.reply.length < 3)
            this.reply += "."
        },
       reload() {
      window.location.reload();
    }
    }
}
</script>

<style>
.ball{
transition: 4s;
 border-radius: 50%;
 height: 600px;
 width: 600px;
 background-color: #000000d6;
  border: 1px #0000009f solid;
  color: rgb(126, 111, 240);
  font-size: 2rem;
  cursor: pointer;
}
.ball:focus{
    animation: shake 0.5s;
}
.ball:hover{
    transition: 2s;
    background-color: #000000;
}
@keyframes shake {
  0% { transform: translate(1px, 1px) rotate(0deg); }
  10% { transform: translate(-1px, -2px) rotate(-1deg); }
  20% { transform: translate(-3px, 0px) rotate(1deg); }
  30% { transform: translate(3px, 2px) rotate(0deg); }
  40% { transform: translate(1px, -1px) rotate(1deg); }
  50% { transform: translate(-1px, 2px) rotate(-1deg); }
  60% { transform: translate(-3px, 1px) rotate(0deg); }
  70% { transform: translate(3px, 1px) rotate(-1deg); }
  80% { transform: translate(-1px, -1px) rotate(1deg); }
  90% { transform: translate(1px, 2px) rotate(0deg); }
  100% { transform: translate(1px, -2px) rotate(-1deg); }
}
</style>