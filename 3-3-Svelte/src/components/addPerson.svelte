<div class="grid-component">
    <input id="firstName" type="text" placeholder="First Name" bind:value={details.firstName}/>
    <input id="lastName" type="text" placeholder="Last Name" bind:value={details.lastName}/>
    <input id="age" type="number" placeholder="Age" bind:value={details.age}/>
    <button on:click={addPerson}>Add Person To Table</button>
</div>
<script>
    import { createEventDispatcher } from "svelte";
        
        const dispatch = createEventDispatcher();
        const details = {
            firstName: '',
            lastName: '',
            age: null
        }
        function addPerson() {
            if(details.firstName && details.lastName && details.age){
            console.log(details)
                dispatch("newPerson", { ...details})
        }}
</script>


<style>
.grid-component {
    padding: 2rem;
}
</style>