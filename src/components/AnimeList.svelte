<script>
    import { onMount } from 'svelte';
    import { goto } from '$app/navigation';
  
    let animeByAirDate = [];
  
    async function fetchAnimeByAirDate() {
      try {
        const response = await fetch('https://anime-api.seirin.icu/api/anime');
        if (response.ok) {
          animeByAirDate = await response.json();
        } else {
          console.error('Failed to fetch anime by air date');
        }
      } catch (error) {
        console.error('Error during fetch:', error);
      }
    }
  
    onMount(() => {
      fetchAnimeByAirDate();
    });
  </script>
  
  <main>
    <h1>Anime List by Air Date</h1>
    {#each animeByAirDate as group}
      <section>
        <h2>{group.year}-{String(group.month).padStart(2, '0')}</h2>
        <ul>
          {#each group.animes as anime}
            <li>
              <strong>{anime.title}</strong><br />
              Image: <img src={anime.image} alt={`${anime.title} poster`} style="max-width: 100px;" /><br />
              Duration: {anime.duration}<br />
              Genre: {anime.genre}<br />
              Production Info: {anime.productionInfo}<br />
              Air Date: {new Date(anime.air_date).toLocaleDateString()}
            </li>
          {/each}
        </ul>
      </section>
    {/each}
  </main>
  
  <style>
    main {
      max-width: 800px;
      margin: 0 auto;
      padding: 1rem;
    }
  
    section {
      margin-bottom: 2rem;
    }
  
    h2 {
      font-size: 1.5rem;
      margin-bottom: 0.5rem;
    }
  
    ul {
      list-style-type: none;
      padding: 0;
    }
  
    li {
      margin-bottom: 1rem;
      padding: 1rem;
      border: 1px solid #ddd;
      border-radius: 4px;
    }
  
    img {
      border-radius: 4px;
    }
  </style>
  
  
  
  