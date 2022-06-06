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
    created() {
        setInterval( () => {
            this.time = new Date().toLocaleTimeString();
        },100)
    }
}
</script>

<style>
    .time {
        transform: scale(5);
        max-width: 400px;
        color: rgb(0, 171, 171);
    }
</style>