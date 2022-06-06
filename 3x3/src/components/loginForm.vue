<template>
	<div class="grid-component">
		<input type="text"  id="username"  v-model="username" placeholder="Enter Username"/>
		<input type="password"  id="password" v-model="password" placeholder="Enter Password"/>
		<button @click="login">Login</button>
		<div class="login" v-if="correct">Log in successful</div>
        <div class="fail" v-else>Enter your username and password (they're both p)</div>
	</div>
</template>

<script>

export default {
    
	data() {
		return {
			username: '',
			password: '',
			correct: false,
			userData: { password: 'p', username: 'p' }
		}
	},
	methods: {
		login() {
            this.correct = 
			(this.password === this.userData.password && 
			this.username === this.userData.username)
			this.reset();
		},
		reset() {
			this.username = '';
			this.password = '';
		}
	}
}

</script>

<style>	
.login {
	color: white;
	background-color: green;
}
</style>