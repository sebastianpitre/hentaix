<script>
    import { onMount } from 'svelte';
  
    let listHentai = [];
    let currentPage = 1;
    const itemsPerPage = 8;
  
    onMount(async () => {
      const response = await fetch("https://tuhentai.onrender.com/animes");
      const results = await response.json();
      listHentai = results;
    });
  
    function recortarTexto(texto) {
      if (texto.length > 40) {
        return texto.slice(0, 40) + "...";
      }
      return texto;
    }
  
    function changePage(page) {
      currentPage = page;
    }
  
    function getCurrentPageItems() {
      const start = (currentPage - 1) * itemsPerPage;
      const end = start + itemsPerPage;
      return listHentai.slice(start, end);
    }
  
    function totalPages() {
      return Math.ceil(listHentai.length / itemsPerPage);
    }
  </script>
  
  <div class="row pt-4">
    {#each getCurrentPageItems() as anime, index}
      {#if index > 0 && index % 4 === 0}
        <div class="col-6 col-sm-4 col-md-4 col-lg-4 col-xl-3 col-xxl-2 p-2">
          <div class="card anuncio border position-relative" style="background-color: #FFD700;">
            <div class="card-body text-center">
              <h4 class="text-dark">Anuncio</h4>
              <p class="text-dark">Este es un anuncio.</p>
            </div>
          </div>
        </div>
      {/if}
      <div class="col-6 col-sm-4 col-md-4 col-lg-4 col-xl-3 col-xxl-2 p-2">
        <div class="card boton border position-relative" style="background-color: #1E1E1E;">
          <div class="card-header p-0 position-relative z-index-2" style="border-radius: 0.75rem 0.75rem 0px 0px">
            <div class="d-block blur-shadow-image cursor-pointer">
              <img src="{anime.url_imagen}" width="100%" height="220vh" alt="img-producto" class="shadow img" style="border-radius: 0.75rem 0.75rem 0px 0px">
            </div>
            <div class="colored-shadow" style="background-image: url('{anime.url_imagen}');"></div>
          </div>
          <div class="card-body py-0">
            <p class="text-white text-center font-weight-bold mt-1 mb-0">{recortarTexto(anime.nombre_anime)}</p>
          </div>
          <div class="mb-n2 mx-2 position-relative">
            <div class="btn col-12 btn-sm btn-danger position-absolute" style="bottom: 0;">Ver ahora</div>
          </div>
        </div>
      </div>
    {/each}
  </div>
  
  <div class="pagination">
    {#if currentPage > 1}
      <button on:click="{() => changePage(currentPage - 1)}">Previous</button>
    {/if}
  
    {#each Array(totalPages()).fill(0) as _, i}
      <button
        class="{currentPage === i + 1 ? 'active' : ''}"
        on:click="{() => changePage(i + 1)}">
        {i + 1}
      </button>
    {/each}
  
    {#if currentPage < totalPages()}
      <button on:click="{() => changePage(currentPage + 1)}">Next</button>
    {/if}
  </div>
  
  <style>
    @media (max-width: 768px) {
      .img {
        height: 220px;
      }
    }
  
    .img {
      filter: blur(3px);
    }
  
    .img:hover {
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
  
    .boton:hover {
      -webkit-box-shadow: 0px 0px 19px 1px rgba(255, 0, 0, 1);
      box-shadow: 0px 0px 19px 1px rgba(255, 0, 0, 1);
      transform: scale(1.05) translateX(1px);
      transform: scale(1.05) translateY(1px);
    }
  
    .anuncio {
      min-height: 150px;
      max-height: 150px;
    }
  
    .pagination {
      display: flex;
      justify-content: center;
      margin-top: 20px;
    }
  
    .pagination button {
      margin: 0 5px;
      padding: 10px 20px;
      border: none;
      background-color: #1E1E1E;
      color: white;
      cursor: pointer;
    }
  
    .pagination button.active {
      background-color: #FFD700;
    }
  
    .pagination button:hover:not(.active) {
      background-color: #555;
    }
  </style>
  