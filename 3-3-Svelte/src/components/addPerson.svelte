<div class="grid-component">
<div class="person-form">
    <form action="javascript:" on:submit={addPerson} ref="addTo">
        <div>
            <input id="firstName" type="text" placeholder="First Name"/>
        </div>
        <div>
            <input id="lastName" type="text" placeholder="Last Name"/>
        </div>
        <div>
            <input id="age" type="text" placeholder="Age"/>
        </div>
        <input type="submit" value="Add person to table" />
    </form>
</div>
</div>

<script>
	import { createEventDispatcher } from "svelte";

    const dispatch = createEventDispatcher();

    function addPerson(){
        const details = {
		firstName : document.getElementById("firstName").value,
		lastName : document.getElementById("lastName").value,
		age : document.getElementById("age").value
		}
        if(details.firstName && details.lastName && details.age)
        dispatch("newPerson", {
            details
        })
    }
</script>

<style>
    .grid-component {
   flex: 1 1 30%;
  }
</style>