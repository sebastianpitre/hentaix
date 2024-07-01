<!-- Modal.svelte -->
<script>
    export let isOpen = false;
    export let anime = {};

    const closeModal = () => {
        isOpen = false;
    }
</script>

{#if isOpen}
    <div class="modal show d-block" tabindex="-1" style="background: rgba(0,0,0,0.5);">
        <div class="modal-dialog">
            <div class="modal-content">
                <div class="modal-header">
                    <h5 class="modal-title">{anime.nombre}</h5>
                    <button type="button" class="btn-close" aria-label="Close" on:click={closeModal}></button>
                </div>
                <div class="modal-body">
                    <img src={anime.imagen} alt="Imagen del Anime" class="img-fluid mb-3">
                    <p>{anime.descripcion}</p>
                </div>
                <div class="modal-footer">
                    <button type="button" class="btn btn-secondary" on:click={closeModal}>Cerrar</button>
                </div>
            </div>
        </div>
    </div>
{/if}

<style>
    .modal.show {
        display: block;
    }
</style>
