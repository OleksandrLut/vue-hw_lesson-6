<template>
   <div class="container">
      <label>
         {{ title }}
         <input ref="userAge" type="number"
         v-model="myValue"
         >
      </label>
      <div class="warn" v-if="isWarningVisible">Значення не може бути більше за 150</div>
   </div>
</template>

<script>
   export default {
      name: 'MyInput',
      props: {
         title: {
            type: String,
            default: ''
         },
         modelValue: {
            type: Number,
         },
         modelModifiers: {
            default: () => ({})
         },
      },
      computed: {
         myValue: {
            get() {
               return this.modelValue
            },
            set(newValue) {
               if (this.modelModifiers.check) {
                  if (newValue > 150) 
                  newValue = null
               }
               if (this.modelModifiers.setColor) {
                  if (newValue > 0) {
                     if (newValue < 10)
                     this.$refs.userAge.style.backgroundColor = "green";
                     else if (newValue < 21)
                     this.$refs.userAge.style.backgroundColor = "yellow";
                     else if (newValue < 150)
                     this.$refs.userAge.style.backgroundColor = "orange";
                  }
                  else
                  this.$refs.userAge.style.backgroundColor = "transparent";
               }
               this.$emit('update:modelValue', newValue)
            },
         },
         isWarningVisible() {
            return this.myValue === null
         }
      },
      // methods: {
      //    setColorStyle() {
            
      //    }
      // },
   }
</script>

<style lang="css" scoped>
input {
   padding: 5px 10px;
   border-radius: 6px;
   background-color: transparent;
   border: 1px solid #000;
   font-size: 20px;
}
.container {
   font-size: 20px;
}
.warn{
   color: red;
   font-size: 18px;
}
</style>