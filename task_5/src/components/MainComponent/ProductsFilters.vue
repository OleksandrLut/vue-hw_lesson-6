<template>
   <div class="filters">
      <div class="filters__body">
         <div class="filters__seller seller-filter">
            <button class="filters__title" @click="onClickSeller">Продавець</button>
            <form class="seller-filter__body" v-show="isVisible">
               <label>
                  <input
                     type="radio"
                     id="rozetka"
                     name="seller"
                     value="rozetka"
                     v-model="sellerInput"
                  />
                  <span>Rozetka</span>
               </label>
               <label>
                  <input
                     type="radio"
                     id="other-sellers"
                     name="seller"
                     value="ather"
                     v-model ="sellerInput"
                  />
                  <span>Інші продавці</span>
               </label>
            </form>
         </div>
         <div class="filters__brand">
            <h2 class="filters__title">Бренд</h2>
            <form class="brand-filter__body">
               <label v-for="(brand, index) in brandsList" :key="index">
                  <input 
                  type="radio"
                  :id="brand"
                  name="brand"
                  :value="brand"
                  v-model ="brandInput"
                  >
                  <span>{{ brand }}</span>
               </label>
            </form>
         </div>
         <!-- <div>продавець: {{ sellerInput }}</div> -->
      </div>
   </div>
</template>

<script>
   export default {
      name: 'ProductsFilters',
      props: {
         seller: {
            type: String,
         },
         brand: {
            type: String
         },
         brandsList: {
            type: Array, 
            required: true
         },
         isVisible: {
            default: false,
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
         onClickSeller() {
            this.$emit('onClickSeller');
         },
      },
   };
</script>

<style lang="scss" scoped>
.filters {
   border-top: 1px solid rgba(128, 128, 128, 0.3);
   border-right: 1px solid rgba(128, 128, 128, 0.3);
   border-bottom: 1px solid rgba(128, 128, 128, 0.3);
   min-height: 600px;
   // .filters__body
   &__body {
      padding: 10px;
   }
   // .filters__seller
   &__seller {
      margin-bottom: 30px;
   }
   // .filters__title
   &__title {
      margin-bottom: 20px;
      font-weight: 600;
   }
   // .filters__brand
   &__brand {
   }
}
.seller-filter {
   // .seller-filter__body
   &__body {
      padding-left: 10px;
      display: flex;
      flex-direction: column;
      gap: 10px;
      label {
         input {
            margin-right: 10px;
         }
      }
   }
}

.brand-filter {

// .brand-filter__body

&__body {
   display: flex;
   flex-direction: column;
   gap: 10px;
   label {
      display: flex;
      align-items: center;
      gap: 10px;
      padding-left: 10px;
   }
}
}



</style>