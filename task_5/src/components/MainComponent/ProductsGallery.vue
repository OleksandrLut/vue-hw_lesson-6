<template>
   <div class="gallery">
      <div class="gallery__body">
         <product-card v-for="card in listData" :key="card.id" :card-data="card" />
      </div>
   </div>
</template>

<script>
import ProductCard from './ProductCard.vue';

   export default {
      name: 'ProductsGallery',

      props: {
      listData: {
         type: Array,
         default: () => []
      },
   },
   components: { ProductCard }
   }
</script>

<style lang="scss" scoped>
.gallery {
   border-top: 1px solid rgba(128, 128, 128, 0.3);
   border-bottom: 1px solid rgba(128, 128, 128, 0.3);
// .gallery__body
&__body {
   padding: 10px 0;
   display: grid;
   grid-template-columns: repeat(auto-fill, 200px);
}
}

</style>