<div class="grid-component">
    <div class="time">
        {time}
    </div>
</div>


<script>
let	time = ''
setInterval(()=>{
    time = new Date().toLocaleTimeString();
    },0)
</script>

<style>
    .grid-component {
        flex: 1 1 30%; margin: 5px; 
        padding: 2rem;
    }
    .time {
        color: rgb(0, 171, 171);
    }
</style>