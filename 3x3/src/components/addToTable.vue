<template>
		<div class="person-form">
			<form action="javascript:" v-on:submit="addPerson()" ref="addTo">
				<div>
					<input id="firstName" type="text" placeholder="First Name"/>
				</div>
				<div>
					<input id="lastName" type="text" placeholder="Last Name"/>
				</div>
				<div>
					<input id="age" type="number" placeholder="Age"/>
				</div>
				<input type="submit" value="Add person to table"/>
			</form>
	    </div>
</template>

<script>
export default {
    data(){
    },
methods: {
	
    addPerson(){
		const details = {
		firstName : document.getElementById("firstName").value,
		lastName : document.getElementById("lastName").value,
		age : document.getElementById("age").value
		}
		if(details.firstName && details.lastName && details.age)
       this.$emit("add", details)
       console.log(details)
    }
}
}
</script>


<style>

</style>