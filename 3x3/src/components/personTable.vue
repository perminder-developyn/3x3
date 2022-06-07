<template>
	<div class="grid-component">
		<div class="form-container">
			<tr>
				<th>First Name</th>
				<th>Last Name</th>
				<th>Age</th>
			</tr>
            <tr v-for="(row, index) in peopleData" :key="index">
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
	data() {
        return {
			peopleData: this.information
		}
	},
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