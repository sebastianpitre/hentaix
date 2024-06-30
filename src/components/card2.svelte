<script>
    import { onMount } from 'svelte';
  
    let listHentai = [];
  
    // Fetch data from the API
    onMount(async () => {
      const response = await fetch("https://tuhentai.onrender.com/animes");
      const results = await response.json();
      listHentai = results;
    });
  
    // Function to trim the text if it exceeds 40 characters
    function recortarTexto(texto) {
      if (texto.length > 40) {
        return texto.slice(0, 40) + "...";
      }
      return texto;
    }
  </script>
  
  
  
  <h3 class="text-white mt-5">Lo más popular</h3>
  <div class="row">
    {#each listHentai as anime, index}
      {#if index > 0 && index % 6 === 0}
        <div class="col-6 col-sm-4 col-md-4 col-lg-4 col-xl-3 col-xxl-2 p-2">
          <div class="carta boton position-relative">
            <div class="card-header p-0 position-relative z-index-2" style="border-radius: 0.75rem 0.75rem 0px 0px">
                <div class="d-block blur-shadow-image p-2 cursor-pointer">
                  <img src="{anime.url_imagen}" width="100%" height="220" alt="img-producto" class="shadow mt-3 img">
                </div>
                <div class="colored-shadow" style="background-image: url('{anime.url_imagen}');"></div>
              </div>
            <div class="card-body text-center px-2">
              <h3 class="text-warning">Anuncio</h3>
              <p class="text-white">¿Por qué veo este anuncio?</p>
            </div>
          </div>
        </div>
      {/if}
      <div class="col-6 col-sm-4 col-md-4 col-lg-4 col-xl-3 col-xxl-2 p-2">
        <div class="carta boton position-relative">
          <div class="card-header p-0 position-relative z-index-2" style="border-radius: 0.75rem 0.75rem 0px 0px">
            <div class="d-block blur-shadow-image p-2 cursor-pointer">
              <img src="{anime.url_imagen}" width="100%" height="280vh" alt="img-producto" class="shadow img">
            </div>
            <div class="colored-shadow" style="background-image: url('{anime.url_imagen}');"></div>
          </div>
          <div class="card-body px-2">
            <p class="text-white mt-1 mb-0">{recortarTexto(anime.nombre_anime)}</p>

            <p class="text-gray mb-0">Sub | Dob</p>
            
          </div>
        </div>
      </div>
    {/each}
  </div>
  

  <style>
    @media (max-width: 768px) {
      .img {
        height: 220px;
      }
    }
  
    .col-xxl-pitre {
      flex: 0 0 auto;
      width: 20%;
    }
    .img {
      filter: blur(0px);
    }
  
    .img:hover {
      filter: blur(0px);
    }
  
    .carta {
      min-height: 380px;
      max-height: 380px;
      display: flex;
      flex-direction: column;
      --hover-shadow-size: 0.5rem;
    }
  
    .boton {
      transition: transform 0.3s ease, background-color 0.3s ease;
      cursor: pointer;
    }
  
    .boton:hover {
     background-color: rgba(71, 71, 71, 0.329);
    }
  
  </style>