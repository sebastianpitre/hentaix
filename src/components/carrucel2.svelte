<script>
  import { onMount } from 'svelte';
  let listHentai = [];
  
  // Fetch data from the API
  onMount(async () => {
    const response = await fetch("https://tuhentai.onrender.com/animes");
    const results = await response.json();
    listHentai = results;
  });
</script>
<header class=" p-0">
    <div id="carouselExampleInterval" class="carousel slide" data-bs-ride="carousel">
      <div class="carousel-inner">
        <div class="carousel-item active" data-bs-interval="5000">
          <div class="page-header min-vh-50" style="background-image: url(&quot;./bg.jpeg&quot;); background-position-y: 50%; background-size: cover; background-position-x: 50%;">
            <span class="mask opacity-8" style="background-color: #000;"></span>
            <div class="container">
              <div class="row justify-content-center">
                <div class="col-lg-8 text-center mx-auto">
      
                  <div class="card-body text-center px-2">
                    <h1 class="text-warning">TuHentaix</h1>
                    <p class="text-white">Disfruta de todo nuestro contenido <br> gratis aqui en TuHentaix!</p>
                  </div>
                  
                </div>
              </div>
            </div>
            
          </div>
        </div>

        {#each listHentai as anime}
        <div class="carousel-item" data-bs-interval="2000">
          <div class="page-header min-vh-50" style="background-image: url(&quot;{anime.url_imagen}&quot;); background-position-y: 0%; background-size: cover; background-position-x: 50%;">
            <span class="mask opacity-8" style="background-color: #000;"></span>
            <div class="container">
              <div class="row justify-content-center">
                <div class="col-lg-8 text-center mx-auto my-auto">
      
                  <div class="card-body text-center px-2">
                    <h1 class="text-warning">{anime.nombre_anime}</h1>
                    <p class="text-white">Disfruta de todo nuestro contenido <br> gratis aqui en TuHentaix!</p>
                  </div>

                </div>
              </div>
            </div>
            
          </div>
        </div>
        {/each}

      </div>
      <button class="carousel-control-prev" type="button" data-bs-target="#carouselExampleInterval" data-bs-slide="prev">
        <span class="carousel-control-prev-icon" aria-hidden="true"></span>
        <span class="visually-hidden">Previous</span>
      </button>
      <button class="carousel-control-next" type="button" data-bs-target="#carouselExampleInterval" data-bs-slide="next">
        <span class="carousel-control-next-icon" aria-hidden="true"></span>
        <span class="visually-hidden">Next</span>
      </button>
    </div>
  </header>