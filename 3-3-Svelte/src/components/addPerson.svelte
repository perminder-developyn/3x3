<div class="grid-component">
    <div class="person-form">
        <form action="javascript:" on:submit={addPerson} ref="addTo">
            <div>
                <input id="firstName" type="text" placeholder="First Name" bind:value={details.firstName}/>
            </div>
            <div>
                <input id="lastName" type="text" placeholder="Last Name" bind:value={details.lastName}/>
            </div>
            <div>
                <input id="age" type="text" placeholder="Age" bind:value={details.age}/>
            </div>
            <input type="submit" value="Add person to table" />
        </form>
    </div>
</div>
<script>
    import { createEventDispatcher } from "svelte";
        
        const dispatch = createEventDispatcher();
        export const details = {
            firstName: "",
            lastName: "",
            age: ""
        }
        function addPerson() {
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