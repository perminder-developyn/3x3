
	<div class="grid-component">
		<div class="form-container">
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
	</div>


<script>

   function	deleteEntry(index) {
			information.splice(index, 1);
            information = information;
		}

 export let information = {
      type: Array,
      required: true
    }


</script>


<style>
	.grid-component {
		flex: 1 1 30%; margin: 5px; 
		padding: 2rem;
  }
button {
		border: none;
	}
	table, th, td {
		border: 0.1rem solid black;
		margin: auto 0;
		text-align: center;
	}
</style>