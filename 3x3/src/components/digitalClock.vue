<template>
    <div class="grid-component">
        <div class="time">
            {{time}}
        </div>
    </div>
</template>

<script>
export default {
	data () {
		return {
			time: ''
		}
	},
    mounted() {
        setInterval(() => {
            this.time = new Date().toLocaleTimeString();
        }, 1000);
    }
}
</script>

<style>
.time {
    text-align: center;
    font-size: 5rem;
    color: rgb(0, 171, 171);
}
</style>