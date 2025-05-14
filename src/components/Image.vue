<template>
    <div class="image-container">
        <img src="@/assets/imagen.png" alt="">
    </div>
</template>

<script>
export default {

}
</script>

<style>
.image-container {
    width: 100%;
    /* Ocupa todo el ancho del componente */
    height: 100%;
    /* Ocupa todo el alto del componente */
    display: flex;
    justify-content: center;
    align-items: center;
    overflow: hidden;
    /* Evita que la imagen se salga del contenedor */
}

.image-container img {
    max-width: 100%;
    /* La imagen no excederá el ancho del contenedor */
    max-height: 100%;
    /* La imagen no excederá el alto del contenedor */
    object-fit: contain;
    /* Ajusta la imagen manteniendo su proporción */
}
</style>