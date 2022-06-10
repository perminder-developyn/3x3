<div class="grid-component">
	<input type="text"  id="username"  bind:value={username} placeholder="Enter Username"/>
    <input type="password"  id="password" bind:value={password} placeholder="Enter Password"/>
    <button on:click={login}>Login</button>
    {#if correct}
        <div class="login">log in successful</div>
    {:else}
        <div>Enter your username and password (they're both p)</div>
    {/if}
</div>


<script>
let username = '';
let password = '';
let correct = false;
let userData = { password: 'p', username: 'p' };


const login = () => {
    correct = 
	    password === userData.password && 
	    username === userData.username;
    reset();
}
const reset = () => {
    username = '';
    password = '';
}
</script>

<style>
.login {
    color: white;
    background-color: green;
    max-width: fit-content;
}

.grid-component {
    padding: 2rem;
}
</style>