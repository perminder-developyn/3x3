<template>
	<div class="grid-component">
		<div class="form-container">
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
		</div>
	</div>
</template>

<script>
export default {
<<<<<<< HEAD
methods: {
	deleteEntry(index) {
			this.information.splice(index, 1);
		}
},
props: {
   information: {
      type: Array,
      required: true
    },
}
=======
	// delete function isn't working since using props
	methods: {
		deleteEntry(index) {
			this.$emit('delete', index)
		}
	},
	props: {
        information: {
            type: Array,
            required: true
        },
	}
>>>>>>> c4cc5e06b412d70f75ee5effffb0151c56da6a23
}
</script>
<style>
.form-container {
	display: inline;
}
.person-form {
	padding-top: 3rem;
}
</style>