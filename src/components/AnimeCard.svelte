<script>
  export let anime;
</script>

<div class="card">
  <img src={anime.image} alt={`${anime.title} poster`} />
  <h2>{anime.title}</h2>
  <p><strong>Duration:</strong> {anime.duration}</p>
  <p><strong>Genre:</strong> {anime.genre}</p>
  <p><strong>制作信息:</strong> {anime.productioninfo}</p>
</div>

<style>
.card {
  border: 1px solid #ccc;
  padding: 1rem;
  margin-bottom: 1rem;
  width: 300px;
}

.card img {
  max-width: 100%;
  height: auto;
}
</style>



