<template>
  <div class="wrapper">
    <my-input title="Вік користувача:" v-model.check.setColor="newValue"/>
    <div>Вік: {{ newValue }}</div>
  </div>
</template>

<script>
import MyInput from './components/MyInput.vue';

export default {
  name: 'App',
  components: {
    MyInput,
  },
  data() {
    return {
      newValue: '',
    }
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  padding: 100px 0 0;
}
.wrapper{
  max-width: 1470px;
  padding: 0 15px;
  margin: 0 auto;
}
</style>
