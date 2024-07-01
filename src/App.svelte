<script>
	import Card from './components/card.svelte';
  import Carrucel from './components/carrucel.svelte';
  import Carrucel2 from './components/carrucel2.svelte';
  import Header from './components/header.svelte';
  import Paginacion from './components/paginacion.svelte';

</script>



<main>
  <Header/>
   
  <div class="container">

    
    <h3 class="text-white mt-5">Tendencia</h3>
      <Carrucel2/>

      <Card/>
  </div>
  
</main>
