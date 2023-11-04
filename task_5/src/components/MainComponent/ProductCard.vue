<template>
   <a :href="cardData.link" class="card" target="_blank">
      <div class="card__image">
         <img :src="cardData.imgSrc" alt="card-image" class="card__img">
      </div>
      <h3 class="card__title">{{ cardData.title }}</h3>
      <div class="card__pice price">
         <div class="price__old">{{ cardData.oldPrice }} ₴</div>
         <div class="price__new">{{ cardData.price }} ₴</div>
      </div>
   </a>
</template>

<script>
   export default {
      name: 'ProductCard',

      props: {
         cardData: {
            type: Object,
            default: () =>({})
         },
      },
   }
</script>

<style lang="scss" scoped>
.card {
   background-color: #fff;
   display: inline-block;
   border: 1px solid rgba(128, 128, 128, 0.3);
   transition: transform 0.3s ease 0s;
   padding: 30px 5px;
   display: grid;
   row-gap: 30px;
   grid-template-rows: auto 1fr auto;
   &:hover {
      transform: scale(1.04);
      box-shadow: 0 0 6px gray;
   }
   // .card__image
   &__image {
      width: 100%;
      padding: 35%;
      position: relative;
   }
   // .card__img
   &__img {
      width: 100%;
      height: 100%;
      object-fit: contain;
      position: absolute;
      top: 0;
      left: 0;
   }
   // .card__contet
   &__contet {
   }
   // .card__title
   &__title {
      font-size: 18px;
      font-weight: 500;
   }
   // .card__pice
   &__pice {
   }
   }
   .price {
   // .price__old
   &__old {
      font-size: 20px;
      color: gray;
      text-decoration: line-through;
      margin-bottom: 15px;
   }
   // .price__new
   &__new {
      font-size: 24px;
      font-weight: 500;
      color: rgb(255, 0, 17);
   }
}

</style>