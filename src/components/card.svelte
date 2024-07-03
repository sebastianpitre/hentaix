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
  
  
  
  
  <div class="row">
    <h3 class="text-white" style="z-index: 10;">Lo más popular</h3>
    {#each listHentai as anime, index}
      {#if index > 0 && index % 7 === 0}
        <div class="col-6 col-sm-4 col-md-4 col-lg-4 col-xl-3 col-xxl-2 px-0 my-1">
          <div class="carta boton position-relative" style="background-color: #333;">
            <div class="card-header p-0 position-relative z-index-2" style="border-radius: 0.75rem 0.75rem 0px 0px">
                <div class="d-block blur-shadow-image p-2 cursor-pointer">
                  <script type='text/javascript' src='//pl23668302.highrevenuenetwork.com/08/8e/52/088e52164e2b475c77773ff04e84d849.js'></script>
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

      {#if index > 0 && index % 20 === 0}
      <!-- <header class="mt-5">
        <div class="page-header min-vh-45" style="background-image: url(&quot;{anime.url_imagen}&quot;); background-position-y: 50%; background-size: cover; background-position-x: 50%;">
          <span class="mask opacity-8" style="background-color: #000;"></span>
          <div class="container">
            <div class="row justify-content-center">
              <div class="col-lg-8 text-center mx-auto my-auto">
    
                
                  <h1 class=" text-white text-hentai mx-auto" style="font-size: 90px;">TuHentaix</h1>
                  <p class="text-white">Disfruta de los mejores hentai totalmente gratis</p>
                
    
    
              </div>
            </div>
          </div>
          <div class="position-absolute w-100 z-index-1 bottom-0">
            
            <svg class="waves" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" viewBox="0 24 150 40" preserveAspectRatio="none" shape-rendering="auto">
              <defs>
                <path id="gentle-wave" d="M-160 44c30 0 58-18 88-18s 58 18 88 18 58-18 88-18 58 18 88 18 v44h-352z"></path>
              </defs>
              <g class="moving-waves">
    
              </g>
            </svg>
          </div>
        </div>
      </header> -->

      <div class="bg-gradient-warning mt-5" style="background-image: url(&quot;./bg.jpeg&quot;); background-position-y: 0%; background-size: cover; background-position-x: 50%;">
        <div class="col-11 my-5 mx-auto " style="background-color: #000;">
          <div class="row py-4">
            <div class="col-xl-5 col-md-8 text-md-end text-center px-5 position-relative">
              <img class="img border-radius-md max-width-300 w-md-60 position-relative z-index-2 mt-n6 mb-xl-n6" src="{anime.url_imagen}" style="border: 5px solid #000;">
            </div>
      
            <div class="col-xl-6 col-12 px-xl-0 px-5 mt-4 my-xl-auto">
              <h3 class="text-white mt-xl-0 mt-5">{anime.nombre_anime}</h3>
              <p class="text-white text-sm mb-0"><span class="text-warning font-weight-bold">Hentai</span> • Sub | Dob</p>
              <p class="text-sm text-white opacity-8">Developers and Companies around the world using our products. Lorem ipsum dolor sit amet consectetur adipisicing elit. Saepe ullam odio, quidem laboriosam eaque ab quaerat, sunt distinctio minus nostrum eveniet omnis, provident quos. Earum minus aut quod. Sequi, voluptas?</p>
              <a href="{anime.urls_adicionales}" class=" btn btn-sm btn-outline-warning icon-move-right text-sm">▶ Comenzar a ver</a>
            </div>
          </div>
        </div>
      </div>
      
      {/if}
      {#if index > 0 && index % 10 === 0}
      <h3 class="text-white mt-4" >Porque viste {recortarTexto(anime.nombre_anime)}</h3>
      {/if}
      <div class="col-6 col-sm-4 col-md-4 col-lg-4 col-xl-3 col-xxl-2 px-0 my-1">
        <div class="carta d-flex flex-column boton position-relative">
          <div class="card-header p-0 position-relative z-index-2" style="border-radius: 0.75rem 0.75rem 0px 0px">
            <div class="d-block blur-shadow-image p-2 cursor-pointer">
              <img src="{anime.url_imagen}" width="100%" height="280vh" alt="img-producto" class="shadow img">
            </div>
            <div class="colored-shadow" style="background-image: url('{anime.url_imagen}');"></div>
          </div>
          <div class="card-body px-2">
            <p class="text-white mt-1 mb-0">{recortarTexto(anime.nombre_anime)}</p>

            <div class="row position-absolute bottom-0 ">
                <div class="col-auto">
                    <a href="{anime.urls_adicionales}" class="mt-auto btn btn-outline-warning icon-move-right text-sm" style="line-height: 0.5;">▶ Ver</a>
                </div>
                <div class="col-auto">
                    <p class="text-white text-sm mt-1">Sub | Dob</p>
                </div>
            </div>
            
            
            
          </div>
        </div>
      </div>
    {/each}
  </div>
  

  <style>
    @media (max-width: 768px) {
      .img {
        height: 260px;
      }
      .carta {
      min-height: 280px;
      max-height: 280px;
    }
    }
  
    .img {
      filter: blur(0px);
    }
  
    .img:hover {
      filter: blur(0px);
    }
  
    .carta {
      min-height: 400px;
      max-height: 400px;
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