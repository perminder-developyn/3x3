<div class="grid-component">
	<tr>
		<th>First Name</th>
		<th>Last Name</th>
		<th>Age</th>
	</tr>
	{#each information as row, index}
		<tr>
			<td>{row.firstName}</td>
			<td>{row.lastName}</td>
			<td>{row.age}</td>
			<td>
				<button on:click={()=>deleteEntry(index)}>x</button>
			</td>
		</tr>
	{/each}
</div>


<script>
const deleteEntry = (index) => {
	information.splice(index, 1);
	information = information;
}

export let information = {
      		type: Array,
      		required: true
};
</script>


<style>	
table, th, td {
	border: 0.1rem solid black;
	margin: auto 0;
text-align: center;
}

.grid-component {
    padding: 2rem;
}
</style>