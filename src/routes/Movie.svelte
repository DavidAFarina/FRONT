<script>
  import { get } from "svelte/store";

	//let promise1 = getFavoritos();
	async function getFavoritos() {
    // faz um request GET para endpoint /favoritos
		const res = await fetch(`http://127.0.0.1:8000/favoritos/?user_id=1`);
		const text = await res.json();
	//Testa se existe filmes nos favoritos e extrai o JSON	
	// 	if (res.ok) {
	// 		alert(JSON.stringify(res.ok)) 
	// 		alert('Existem filmes nos favoritos');

			
			
	// 		return text; 
	// 	} 
    // else { 
	// 	alert('Nao tem filmes nos favoritos');
	// 	throw new Error(text);
	// }

	
	
		}



	let promise = getFilmes();
	async function getFilmes() {
    // faz um request GET para endpoint /filmes
		const res = await fetch(`http://localhost:8000/filmes`);
		const text = await res.json();
		if (res.ok) { return text; } 
    else { throw new Error(text);}
	
		}

	
	function handleClick() {
		promise = getFilmes();
		getFavoritos();
	}


	
	
	async function setFav(tmdb_id) {
		let data = {}
		data.user_id = 1
		data.tmdb_id = tmdb_id 
		//24428
		
		// alert(tmdb_id) 
    // faz um POST para endpoint /filmes
		const res = await fetch(`http://127.0.0.1:8000/favoritos`,
		{
            method: 'POST',
            headers: {
                'Content-Type': 'application/json'
            },
            body: JSON.stringify(data)
        });
        const json = await res.json();
        let resposta = JSON.stringify(json);
		window.location.reload()
		

		
		
		//alert para informar se o filme foi adicionado aos favoritos ou se ocorreu algum erro.
		if (res.ok) {
			alert('Filme adicionado aos favoritos com sucesso!');
		} else {
			alert('Erro ao adicionar filme aos favoritos.');
		}
	}

	async function deleteFav(tmdb_id) {
		let data = {}
		data.user_id = 1
		data.tmdb_id = tmdb_id 
		
		//24428
		
		//alert(tmdb_id) 
    // faz um DELETE para endpoint /filmes
		const res = await fetch(`http://127.0.0.1:8000/favoritos/${tmdb_id}`,
		{
            method: 'DELETE',
            headers: {
                'Content-Type': 'application/json'
            },
            body: JSON.stringify(data)
        });
        const json = await res.json();
        let resposta = JSON.stringify(json);
		window.location.reload()
		

		//alert para informar se o filme foi excluido dos favoritos ou se ocorreu algum erro.
		if (res.ok) {
			alert('Filme excluido dos favoritos com sucesso!');
		} else {
			alert('Erro ao excluir filme dos favoritos.');
		}
	}


	
</script>

<div id="componente-movie">

<button on:click={handleClick}> Get filmes </button>

{#await promise}
	<p>...loading</p>
	{:then filmes}
		<h3>Lista de filmes</h3>		
		{#each filmes as filme}
    <div class="grid">
		<h5>{filme.ID}</h5>
		<h5>{filme.title}</h5>
	</div>


	

    <div class="grid">
	  	<img src="{filme.image}" alt="" position>
		  <div class="grid">
			<div class="grid">
				{#if filme.is_fav === false}
				<p>
					<button type="button" on:click={() => setFav(filme.ID)}>Favoritar</button>
															
				</p>
				{:else}
				<p>					
					<button type="button" on:click={() => deleteFav(filme.ID)}>Desfavoritar</button>
				</p>
				{/if}
			</div>

		</div>
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

