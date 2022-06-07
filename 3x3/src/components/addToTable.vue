<template>
	<div class="person-form">
		<input id="firstName" type="text" placeholder="First Name" v-model="firstName"/>
		<input id="lastName" type="text" placeholder="Last Name" v-model="lastName"/>
		<input id="age" type="number" placeholder="Age" v-model="age"/>				
		<button @click="addPerson">Add Person To Table</button>
	</div>
</template>

<script>

export default {	
	data() {
        return {
            firstName: '',
			lastName: '',
			age: null         
        }
    },
	methods: {
		addPerson(){
			const details = {
				firstName: this.firstName, 
				lastName: this.lastName, 
				age: this.age 
			}
		if(details.firstName && details.lastName && details.age)
			this.$emit("add", details)
    	}
	}
}
</script>
