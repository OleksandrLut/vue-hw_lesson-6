<template>
   <custom-input 
      title="Імя користувача:"
      type="text"
      placeholder ="Введіть імя..."
      v-model="userName"
   />
</template>

<script>
import CustomInput from './CustomInput.vue';

export default {
   name: "UserNameInput",
   components: {
      CustomInput,
   },
   props: {
      modelValue:{
         type: String,
      },
      modelModifiers: {
         default: () => ({})
      },
   },
   computed: {
      userName: {
         get() {
            return this.modelValue
         },
         set(newValue){
            this.$emit('update:modelValue', newValue)
         }
      }
   },
};
</script>

<style lang="scss" scoped>

</style>