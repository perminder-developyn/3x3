<template>
				<tr>
					<th>First Name</th>
					<th>Last Name</th>
					<th>Age</th>
				</tr>
                <tr v-for="(row, index) in information" :key="index">
					<td>{{ row["firstName"] }}</td>
					<td>{{ row["lastName"] }}</td>
					<td>{{ row["age"] }}</td>
					<td>
						<button v-on:click="deleteEntry(index)">x</button>
					</td>
				</tr>


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
			<input type="submit" value="Add person to table" />
		</form>
</template>

<script>
export default {
    data(){
        return{
            information:[
                {
            firstName:'chik',
            lastName: 'sdasd',
            age: 22,
            },
            {
            firstName:'chike',
            lastName: 'sdasdsdsd',
            age: 55,
            }
            ],
            person: {firstName:'',
                     lastName:'',
                     age: null
                     }
            
        }
    },
methods: {
	deleteEntry(index) {
			this.information.splice(index, 1);
		},
    addPerson(){
		const details = {
		firstName : document.getElementById("firstName").value,
		lastName : document.getElementById("lastName").value,
		age : document.getElementById("age").value
		}
		if(details.firstName && details.lastName && details.age)
       this.information.push(details); this.$refs.addTo.reset()
    }
}
}
</script>
<style>
</style>