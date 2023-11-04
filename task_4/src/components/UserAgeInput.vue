<template>
   <custom-input 
      title="Вік користувача:"
      type="number"
      placeholder ="Введіть вік..."
      v-model="userAge"
   />
</template>

<script>
import CustomInput from './CustomInput.vue';

export default {
   name: "UserAgeInput",
   components: {
      CustomInput,
   },
   props: {
      modelValue:{
         type: Number,
      },
      modelModifiers: {

      }
   },
   computed: {
      userAge: {
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