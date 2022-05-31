<div class="grid-component">
    <button 
        class="ball" 
        on:click={suspense}>
        {reply}
    </button>
</div>

<script>
let reply = '8';
const replies = [
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
               
           
function randomReply() {
    reply = replies[Math.floor(Math.random()*replies.length)]
    }
function suspense() {
    reply = ""
    setInterval(loader, 500)
    setTimeout(randomReply, 3000)
    setTimeout(reload, 9000)
    }
function loader() {
    if(reply.length < 3)
        reply += "."
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
    .ball {
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
    .ball:focus {
        animation: shake 0.5s;
        }
    .ball:hover {
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