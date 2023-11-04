<template>
   <header class="header">
      <div class="header__container">
         <div class="header__menu">
            <span></span>
         </div>
         <div class="header__logo">
            <img src="../assets/img/logo/logo.svg" alt="logo-rozetka" class="header__img-logo">
         </div>
         <a href="#" class="header__catalog catalog">
            <div class="catalog__icon">
               <img src="../assets/img/icons/catalog_icon.png" alt="catalog-icon" class="catalog__img">
            </div>
            <span>Каталог</span>
         </a>
         <div class="header__search">
            <input type="text" placeholder="Я шукаю...">
            <button>Знайти</button>
         </div>
         <div class="header__languege languege">
            <div class="languege__en">EN</div>
            <div class="languege__ua"><div><span></span><span></span></div>UA</div>
         </div>
         <div class="header__search-icon">
            <a href="#" class="header__link">
               <img src="../assets/img/icons/search_icon.svg" alt="user-search-icon">
            </a>
         </div>
         <div class="header__auth">
            <a href="#" class="header__link">
               <img src="../assets/img/icons/user_icon.png" alt="user-auth-icon">
            </a>
         </div>
         <div class="header__cart">
            <a href="#" class="header__link">
               <img src="../assets/img/icons/shopping_cart_icon.png" alt="shopping-cart-icon">
            </a>
         </div>
      </div>
   </header>
</template>

<script>
   export default {
      name: 'HeaderComponent',
   }
</script>

<style lang="scss" scoped>

.header {
   flex: 0 0 auto;
   background-color: rgb(34, 31, 31);
   padding: 10px 0;
   // .header__container
   &__container {
      max-width: 1440px;
      padding: 0 15px;
      margin: 0 auto;
      display: flex;
      align-items: center;
      justify-content: space-between;
      column-gap: 30px;
      @media (max-width:1060px){
         column-gap: 20px;
      }
      @media (max-width:992px){
         .header__languege,
         .header__catalog {
            display: none;
         }
         .header__logo {
            max-width: 40px;
            overflow: hidden;
         }
      }
      @media (max-width: 530px){
         justify-content: stretch;
         column-gap: 10px;
         // .header__auth {
         //    display: none;
         // }
         .header__search {
            display: none;
         }
         .header__search-icon {
            flex: 1 1 auto;
         }
      }
      @media (min-width: 530px){
         .header__search-icon {
            display: none;
         }
      }
   }
   // .header__menu
   &__menu {
      position: relative;
      width: 34px;
      height: 34px;
      display: flex;
      align-items: center;
      justify-content: center;
      border-radius: 6px;
      transition: background-color 0.4s ease 0s;
      cursor: pointer;
      &:hover {
         background-color: #464242;
      }
      &::after,
      &::before {
         content: '';
         position: absolute;
         width: 20px;
         height: 2px;
         left: 50%;
         transform: translateX(-50%);
         background-color: #fff;
      }
      &::after{
         top: 9px;
      }
      &::before {
         bottom: 9px;
      }
      span {
         width: 20px;
         height: 2px;
         background-color: #fff;
         position: relative;
      }
   }
   // .header__logo
   &__logo {
   }
   // .header__img-logo
   &__img-logo {
   }
   // .header__search
   &__search {
      flex: 1 1 auto;
      display: flex;
      align-items: center;
      input {
         flex: 1 1 auto;
         padding: 9px 20px;
         border-radius: 4px 0 0 4px;
      }
      button {
         flex: 0 0 auto;
         padding: 9px 15px;
         background-color: #00a046;
         border-radius: 0 4px 4px 0;
         color: #fff;
         cursor: pointer;
         transition: background-color 0.4s ease 0s;
         &:hover {
            background-color: #00b24d;
         }
      }
   }
   // .header__languege
   &__languege {
   }
   // .header__auth
   &__auth {
      
   }
   // .header__link
   &__link {
      display: inline-block;
      width: 34px;
      height: 34px;
      padding: 5px;
      border-radius: 4px;
      transition: background-color 0.3s ease 0s;
      &:hover {
         background-color: #464242;
      }
      img {
         width: 100%;
      }
      
   }
   // .header__cart
   &__cart {
   }
   // .header__link-cart
   &__link-cart {
   }
}
.languege {
   color: #fff;
   font-weight: 500;
   display: flex;
   align-items: center;
   column-gap: 20px;
   
   // .languege__en
   &__en {
      cursor: pointer;
      position: relative;
      transition: color 0.3s ease 0s;
      &:not(:last-child) {
         &::after {
            content: '';
            width: 2px;
            height: 20px;
            background-color: #fff;
            position: absolute;
            top: 50%;
            right: -10px;
            transform: translateY(-50%);
         }
      }
      &:hover {
         color: #eaff04;
      }
   }
   // .languege__ua
   &__ua {
      cursor: pointer;
      transition: color 0.3s ease 0s;
      &:hover {
         color: #eaff04;
      }
      display: flex;
      align-items: center;
      gap: 5px;
      div{
         width: 16px;
         height: 16px;
         display: flex;
         flex-direction: column;
         border-radius: 50%;
         overflow: hidden;
         transform: translateY(-2px);
         span{
            flex: 0 0 50%;
            width: 16px;
         }
         & :nth-child(1) {
            background-color: rgb(46, 85, 242);
            
         }
         & :nth-child(2) {
            background-color: #eaff04;
         }
      }
   }
}
.catalog {
   display: flex;
   align-items: center;
   gap: 10px;
   background-color: #fff3;
   padding: 6px 15px;
   border-radius: 6px;
   transition: background-color 0.3s ease 0s;
   &:hover {
      background-color: rgba(255, 255, 255, 0.5);
   }
   // .catalog__icon
   &__icon {
      width: 30px;
      height: 30px;
   }
   // .catalog__img
   &__img {
      width: 100%;
   }
   span {
      color: #fff;
   }
}

</style>