<template>
			<form action="javascript:" v-on:submit="login()">
            <p>username and password :  'p'</p>
				<input type="text"  id="username"  v-model="username" placeholder="p"/>
				<input type="password"  id="password" v-model="password" placeholder="p"/>
				<input type="submit"/>
			</form>
			<div class="login" v-if="correct">log in successful</div>
            <div class="fail" v-if="fail">try again</div>
	
</template>

<script>

export default {
    
	data() {
		return {
			username: "",
			password: "",
			correct: false,
            fail: false
		}
	},
	methods: {
		login() {
            this.fail = false;
            this.correct = false;
			if ((this.username && this.password === "p")) {
				this.correct = true;
			}else{
                this.fail = true;
            }
		}
	}
}

</script>

<style>
.login{
	color: white;
	background-color: green;
}
</style>