<script>
	let promise = getUsers();
	async function getUsers() {
    // faz um request GET para endpoint /usuarios
		const res = await fetch(`http://localhost:8000/users`);
		const text = await res.json();
		if (res.ok) { return text; } 
    else { throw new Error(text);}
	}
	function handleClick() {
		promise = getUsers();
	}
    // deleteuser(id)
    async function delete_user(id) {
		const res = await fetch(
            `http://localhost:8000/user/delete/${id}`, {
                method: 'DELETE',
                headers: {
                'Content-Type': 'application/json'
            },
            });
		const text = await res.json();
		if (res.ok) { 
            promise = getUsers()
            return text; } 
    else { throw new Error(text);}
	}

</script>

<div id="componente-movie">

<button on:click={handleClick}> Get filmes </button>

{#await promise}
	<hp>...loading</hp>
	{:then users}
		<h4>Lista de usuarios</h4>		
		{#each users as user}
    <div class="grid">
        <p>{user.id}</p>
        <p>{user.name}</p>
        <p>{user.email}</p>
        <p><button on:click={()=>delete_user(user.id)}>Delete</button></p>
        
        
    </div>
		{/each}
	{:catch error}
		<p style="color:red">{error.message}</p>
{/await}

</div>

<style>
  p{ font-weight: bold; font-size: 2em}
  .grid{ padding: 10px; display: grid; grid-template-columns: 1fr 2fr; }
div{
  background-color: rgb(212, 253, 230);
}
</style>