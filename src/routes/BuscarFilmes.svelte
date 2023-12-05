

<form class="crud" on:submit|preventDefault={sendForm}>
    <input type="text" id="title" name="title" placeholder="Título do Filme" required autocomplete="off">
    
    <input type="submit" value="buscar">
</form>




<script>

    let filmes = [];
    let promise = sendForm();
    async function sendForm(){
        
       
        const title = document.getElementById("title").value;
        
        const res = await fetch(`http://127.0.0.1:8000/filme/${title}`);
       
        
        const json = await res.json();
        filmes = json;
        
        console.log(title);
        
       
    }
    
</script>

{#if filmes.length > 0}
    <h1>Lista dos Filmes</h1>
    {#each filmes as filme}
        <p>ID do Filme: <b>{filme.id}</b></p>
        <p>Nome do Filme: <b>{filme.title}</b></p>
        <img src="{filme.image}" alt="">
        
        {#if filme.is_fav === false}
				<p>
					<button type="button" on:click={() => setFav(filme.ID)}>Favoritar</button>											
				</p>
				{:else}
				<p>					
					<button type="button" on:click={() => deleteFav(filme.ID)}>Desfavoritar</button>
				</p>
				{/if}
                <hr>
    {/each}
{:else}
    <p>Nenhum filme encontrado.</p>
{/if}
  