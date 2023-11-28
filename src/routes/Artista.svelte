
<script>
    let data = {
      "biography": "Arnold Alois Schwarzenegger (born July 30, 1947) is an Austrian-American actor, film producer, businessman, former bodybuilder and politician who served as the 38th governor of California (2003-2011). As of 2022, he is the most recent Republican governor of California. Time magazine named Schwarzenegger one of the 100 most influential people in the world in 2004 and 2007. He also served as ...",
      "birthday": "1947-07-30",
      "gender": 2,
      "id": 1100,
      "known_for_department": "Acting",
      "name": "Arnold Schwarzenegger",
      "place_of_birth": "Thal, Styria, Austria",
      "popularity": 26.296,
      "profile_path": "/zEMhugsgXIpnQqO31GpAJYMUZZ1.jpg"
    }
    </script>
    
    <h2>{data.name}</h2>
    
    <p>{data.biography}</p>
    <img src="https://image.tmdb.org/t/p/w185{data.profile_path}"/>


	  <!-- <script>
	        let promise = getArtista();
	        async function getArtista() {
	        // faz um request GET para endpoint /filmes
	            const res = await fetch(`http://localhost:8000/artista`);
	            const text = await res.json();
	            if (res.ok) { return text; } 
	        else { throw new Error(text);}
	        }
	        function handleClick() {
	            promise = getArtista();
	        }
	    </script>
{/await}
<script>
	let promise = getArtista();
	async function getArtista() {
    // faz um request GET para endpoint /usuarios
		const res = await fetch(`http://127.0.0.1:8000/artistas/22529`);
		const text = await res.json();
		if (res.ok) { return text; } 
    else { throw new Error(text);}
	}
    <div id="componente-movie">
    
    <button on:click={handleClick}> Get artista </button>
    
    {#await promise}
        <p>...loading</p>
        {:then filmes}
            <h1>Lista de artistas</h1>		
            {#each filmes as filme}
        <div class="grid">
          <p>{filme.title}</p>
          <img src="{filme.image}" alt="">
        </div>
            {/each}
        {:catch error}
            <p style="color:red">{error.message}</p>
    {/await}
    
    </div>
    
    <style>
      p{ font-weight: bold; font-size: 2em}
      .grid{ padding: 10px; display: grid; grid-template-columns: 1fr 2fr; }
    div{<script>
	        let promise = getArtista();
	        async function getArtista() {
	        // faz um request GET para endpoint /filmes
	            const res = await fetch(`http://localhost:8000/artista`);
	            const text = await res.json();
	            if (res.ok) { return text; } 
	        else { throw new Error(text);}
	        }
	        function handleClick() {
	            promise = getArtista();
	        }
	    </script>
{/await}
<script>
	let promise = getArtista();
	async function getArtista() {
    // faz um request GET para endpoint /usuarios
		const res = await fetch(`http://127.0.0.1:8000/artistas/22529`);
		const text = await res.json();
		if (res.ok) { return text; } 
    else { throw new Error(text);}
	}
    <div id="componente-movie">
    
    <button on:click={handleClick}> Get artista </button>
    
    {#await promise}
        <p>...loading</p>
        {:then filmes}
            <h1>Lista de artistas</h1>		
            {#each filmes as filme}
        <div class="grid">
          <p>{filme.title}</p>
          <img src="{filme.image}" alt="">
        </div>
            {/each}
        {:catch error}
            <p style="color:red">{error.message}</p>
    {/await}
    
    </div>
    
    <style>
      p{ font-weight: bold; font-size: 2em}
      .grid{ padding: 10px; display: grid; grid-template-columns: 1fr 2fr; }
    div{<script>
	        let promise = getArtista();
	        async function getArtista() {
	        // faz um request GET para endpoint /filmes
	            const res = await fetch(`http://localhost:8000/artista`);
	            const text = await res.json();
	            if (res.ok) { return text; } 
	        else { throw new Error(text);}
	        }
	        function handleClick() {
	            promise = getArtista();
	        }
	    </script>
{/await}
<script>
	let promise = getArtista();
	async function getArtista() {
    // faz um request GET para endpoint /usuarios
		const res = await fetch(`http://127.0.0.1:8000/artistas/22529`);
		const text = await res.json();
		if (res.ok) { return text; } 
    else { throw new Error(text);}
	}
    <div id="componente-movie">
    
    <button on:click={handleClick}> Get artista </button>
    
    {#await promise}
        <p>...loading</p>
        {:then filmes}
            <h1>Lista de artistas</h1>		
            {#each filmes as filme}
        <div class="grid">
          <p>{filme.title}</p>
          <img src="{filme.image}" alt="">
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
    
      background-color: rgb(212, 253, 230);
    }
    </style> 
    
      background-color: rgb(212, 253, 230);
    }
    </style> 
     -->