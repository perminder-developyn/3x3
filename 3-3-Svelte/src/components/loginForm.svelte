<div class="grid-component">
    <form action="javascript:" on:submit={login}>
        <p>username and password :  'p'</p>
		    <input type="text"  id="username"  bind:value={username} placeholder="p"/>
			<input type="password"  id="password" bind:value={password} placeholder="p"/>
			<input type="submit"/>
	</form>
        {#if correct}
	        <div class="login">log in successful</div>
        {:else if fail}
            <div class="fail">try again</div>
        {/if}
</div>


<script>
let username = "";
let password = "";
let correct = false;
let fail = false;

function login() {
    correct = false;
        if(username && password === "p") {
            correct = true;
        }else{
            fail = true;
        }
    }
</script>

<style>
    .login {
        color: white;
        background-color: green;
    }
    .grid-component {
        flex: 1 1 30%; 
        margin: 5px; 
        padding: 2rem;
    }
</style>