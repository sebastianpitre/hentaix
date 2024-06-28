<script>
    let listHentai = [];
    
    // Fetch data from the API
    fetch("https://tuhentai.onrender.com/animes")
      .then((response) => response.json())
      .then((results) => (listHentai = results));
    
    // Function to trim the text if it exceeds 40 characters
    function recortarTexto(texto) {
      if (texto.length > 40) {
        return texto.slice(0, 40) + "...";
      }
      return texto;
    }
  </script>
      
  <div class="row pt-4">
    {#each listHentai as animes}
      <div class="col-6 col-sm-4 col-md-4 col-lg-4 col-xl-3 col-xxl-2 p-2">
        <div class="card boton border position-relative" style="background-color: #1E1E1E;">
          <!-- {#if animes.categoryId === }
            <span class="bg-warning col-6 text-white text-center position-absolute" style="z-index: 3; border-radius: 10px 0px 20px 0px;">new</span>
          {/if} -->
          
          <div class="card-header p-0 position-relative z-index-2" style="border-radius: 0.75rem 0.75rem 0px 0px">
            <div class="d-block blur-shadow-image cursor-pointer">
              <img src="{animes.url_imagen}" width="100%" height="220vh" alt="img-producto" class="shadow img" style="border-radius: 0.75rem 0.75rem 0px 0px">
            </div>
            <div class="colored-shadow" style="background-image: url(&quot;{animes.url_imagen}&quot;);"></div>
          </div>
          
          <div class="card-body py-0 ">
            <p class="text-white text-center font-weight-bold mt-1 mb-0">{recortarTexto(animes.nombre_anime)}</p>

              
          </div>
          <div class="mb-n2 mx-2 position-relative">
            <div class="btn col-12 btn-sm btn-danger position-absolute" style="bottom: 0;">Ver ahora</div>
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
  
    .img{
        filter: blur(3px);
    }

    .img:hover{
        filter: blur(0px);
    }
    .card {
      min-height: 350px;
      max-height: 350px;
    }

    .boton {
      
      transition: transform 0.3s ease, background-color 0.3s ease;
      cursor: pointer;
    }

    /* Efecto hover */
    .boton:hover {

        -webkit-box-shadow: 0px 0px 19px 1px rgba(255,0,0,1);
        box-shadow: 0px 0px 19px 1px rgba(255,0,0,1);
      transform: scale(1.05) translateX(1px); /* Escala y mueve el botón */
      transform: scale(1.05) translateY(1px); /* Escala y mueve el botón */
    }
  </style>
  