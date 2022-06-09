<div class="grid-component">
    <div class="time">
        {time}
    </div>
</div>


<script>
let	time = ''
setInterval(() => {
    time = new Date().toLocaleTimeString();
    }, 1000);
</script>

<style>
.time {
    text-align: center;
    font-size: 5rem;
    color: rgb(0, 171, 171);
}
.grid-component {
    padding: 2rem;
}

</style>