<template>
  <div class="app">
    <CustomInput v-model.check="emailValue" />
    <p>Введений e-mail: {{ emailValue }}</p>
  </div>
</template>

<script>
import CustomInput from "@/components/CustomInput";

export default {
  name: "App",
  components: {
    CustomInput,
  },
  data() {
    return {
      emailValue: "",
    };
  },
};
</script>

<style>
@import './assets/reset.scss';
.app {
  padding: 100px 0 0;
  display: flex;
  flex-direction: column;
  align-items: center;
  height: 100vh;
  background-color: rgb(193, 193, 193);
  font-family: Verdana, Geneva, Tahoma, sans-serif;
}
.app p {
  margin-top: 30px;
  color: gray;
}
</style>
