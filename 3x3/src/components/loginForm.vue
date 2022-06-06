<template>
	<div class="grid-component">
        <p>username and password are both 'p'</p>
		<input type="text"  id="username"  v-model="username" placeholder="Enter Username"/>
		<input type="password"  id="password" v-model="password" placeholder="Enter Password"/>
		<button @click="login">Login</button>
		<div class="login" v-if="correct">log in successful</div>
        <div class="fail" v-if="fail">try again</div>
	</div>
</template>

<script>

export default {
    
	data() {
		return {
			username: '',
			password: '',
			correct: false,
            fail: false,
			userData: { password: 'p', username: 'p'}
		}
	},
	methods: {
		login() {
            this.fail = false;
            this.correct = false;
			if ((this.password === this.userData.password & 
				this.username === this.userData.username)) {
					this.correct = true;
					this.reset();
			} else {
                this.fail = true;
				this.reset();
            }
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