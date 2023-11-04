<template>
  <custom-input 
      title="Імя користувача:"
      type="text"
      placeholder ="Введіть імя..."
      v-model.isNoEmpty="userName"
  />
  <custom-input 
      title="Вік користувача:"
      type="number"
      placeholder ="Введіть вік..."
      v-model.isAgeValid="userAge"
  />

  <div class="user-info"> Імя - {{ userName }}, Вік - {{ userAge }}</div>

</template>

<script>
import CustomInput from './components/CustomInput.vue';

export default {
  name: "App",
  components: {
    CustomInput,
  },
  data() {
    return {
      userName: '',
      userAge: null,
    }
  },
};
</script>

<style lang="scss">
@import './assets/reset.scss';
#app{
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 100vh;
  background-color: gray;
  font-family: Verdana, Geneva, Tahoma, sans-serif;
}
.user-info{
  padding: 10px 30px;
  border-radius: 6px;
  box-shadow: 0 0 6px #000;
}
</style>
