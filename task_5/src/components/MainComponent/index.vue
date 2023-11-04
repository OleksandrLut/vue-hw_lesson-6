<template>
   <main class="page">
      <div class="page__container">
         <h1 class="page__title">Ноутбуки</h1>
         <div class="page__body">
            <products-filters 
            v-model:seller = "sellerInput"
            v-model:brand = "brandInput"
            :is-visible="isVisible" 
            :brands-list="brandsList"
            @onClickSeller="onClickSeller" 
            />
            <products-gallery 
            :list-data="listData" 
            />
         </div>
      </div>
      
   </main>
</template>

<script>
   import ProductsFilters from './ProductsFilters.vue';
   import ProductsGallery from './ProductsGallery.vue';

   export default {
      name: 'MainComponent',
      components: { 
         ProductsFilters,
         ProductsGallery
      },
      data() {
         return {
            isVisible: false,
         };
      },
      props: {
         listData: {
            type: Array,
            default: () => []
         },
         brandsList: {
            type: Array, 
            required: true
         },
         seller: {
            type: String,
         },
         brand: {
            type: String
         },
      },
      computed: {
         sellerInput: {
            get() {
               return this.seller;
            },
            set(newValue) {
               this.$emit('update:seller', newValue);
            },
         },
         brandInput: {
            get() {
               return this.brand;
            },
            set(newValue) {
               this.$emit('update:brand', newValue);
            },
         },
      },
      methods: {
         onClickSeller(){
            this.isVisible = this.isVisible ? false : true;
         }
      }
   }
</script>
<style lang="scss" scoped>
.page {
   flex: 1 0 auto;
   padding: 50px 0;
   // .page__container
   &__container {
      max-width: 1440px;
      padding: 0 15px;
      margin: 0 auto;
   }
   // .page__title
   &__title {
      font-size: 34px;
      font-weight: 900;
      margin-bottom: 30px;
   }
   // .page__body
   &__body{
      display: grid;
      grid-template-columns: 250px 1fr;
      // column-gap: 10px;
   }
}

</style>