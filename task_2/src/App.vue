<template>
  <div class="page">
    <div class="page__container">
      <div class="page__body">
        <custom-input 
        title="Ведіть шлях до файлу:"
        v-model.isPassCorrect="urlValue"
        
        />
        <div v-if="urlValue !== ''" class="page__info">URL: {{ urlValue }}</div>
      </div>
    </div>
  </div>
</template>

<script>
import CustomInput from './components/CustomInput.vue';


export default {
  name: "App",
  components: {
    CustomInput
  },
  data() {
    return {
      urlValue: '',
    }
  },
};
</script>

<style lang="scss">
@import './assets/reset.scss';

.page {
  background-color: rgb(205, 203, 203);
  height: 100vh;
  // .page__container
  &__container {
    max-width: 1470px;
    padding: 100px 15px 0;
    margin: 0 auto;
  }
  // .page__body
  &__body {
    padding: 50px;
    background-color: gray;
    border-radius: 6px;
    box-shadow: 0 0 8px #000;
    position: relative;
  }
  &__info {
    position: absolute;
    left: 50px;
    bottom: -70px;
    padding: 20px;
    border-radius: 6px;
    background-color: rgba(255, 255, 255, 0.5);
  }
}


</style>
