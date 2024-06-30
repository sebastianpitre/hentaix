<script>
	import Card from './components/card.svelte';
  import Card2 from './components/card2.svelte';
  import Header from './components/header.svelte';
  import Paginacion from './components/paginacion.svelte';

</script>



<main>
  <Header/>
  <div class="container">

    <h3 class="text-white mt-5">Tendencia</h3>
    <header class="bg-gradient-dark mt-4">
      <div class="page-header min-vh-35" style="background-image: url(&quot;./bg.avif&quot;); background-position-y: 50%; background-size: cover; background-position-x: 70%;">
        <span class="mask bg-gradient-dark opacity-0"></span>
        <div class="container">
          <div class="row justify-content-center">
            <div class="col-lg-8 text-center mx-auto my-auto">
  
            </div>
          </div>
        </div>
        
      </div>
    </header>
       <Card2/>
  </div>
  
</main>
