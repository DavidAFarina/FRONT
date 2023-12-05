

<form class="crud" on:submit|preventDefault={sendForm}>
    <input type="text" id="title" name="title" placeholder="Nome do artista" required autocomplete="off">
    
    <input type="submit" value="buscar">
</form>




<script>

    let artistas = [];
    let promise = sendForm();
    async function sendForm(){
        
       
        const title = document.getElementById("title").value;
        
        const res = await fetch(`http://127.0.0.1:8000/artista/${title}`);
       
        
        const json = await res.json();
        artistas = json;
        
        console.log(title);
        
       
    }
    
</script>

{#if artistas.length > 0}
    <h1>Lista dos Artistas</h1>
    {#each artistas as artista}
        <p>ID do Artista: <b>{artista.id}</b></p>
        <p>Nome do Artista: <b>{artista.name}</b></p>
        <p>Popularidade do Artista: <b>{artista.rank}</b></p>
        <img src="{artista.image}" alt="">
        <!-- <h4>biography do Artista:</h4> <b>{artista.biography}</b> -->
        
        
        
        <hr>
   
    {/each}
{:else}
    <p>Nenhum artista encontrado.</p>
{/if}
  