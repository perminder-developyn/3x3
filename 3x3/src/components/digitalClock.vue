<template>
<div class="clock-wrapper">
<div class="time">
{{time}}
</div>
</div>
</template>

<script>

export default {
    
	data (){
		return {
			time: ''
		}
	},
    created(){
        setInterval(()=>{
            this.time = new Date().toLocaleTimeString();
        },1000)
    }
}

</script>