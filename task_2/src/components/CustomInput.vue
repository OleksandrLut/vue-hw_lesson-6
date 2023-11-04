<template>
   <div class="body">
      <label>
         <span>{{ title }}</span>
         <input ref="inputPass" 
         type="text" 
         :class="{ 'pass-incorrect': !isPassCorrect }"
         v-model="userUrl">
      </label>
   </div>
</template>

<script>
   export default {
      name: 'CustomInput',
      props: {
         title: {
            type: String,
            default: '',
         },
         modelValue: {
            type: String,
         },
         modelModifiers: {
            default: () => ({})
         },
      },
      data() {
         return {
            isPassCorrect: true,
         }
      },
      computed: {
         userUrl: {
            get() {
               return this.modelValue
            },
            set (newValue) {
               if (this.modelModifiers.isPassCorrect) {
                  if (this.isUserPassCorrect(newValue)) {
                     this.isPassCorrect = true;
                  } else {
                     if(newValue !== '')
                     this.isPassCorrect = false;
                     else
                     this.isPassCorrect = true;
                  }
               }
               this.$emit('update:modelValue', newValue);
            }
         }
      },
      methods: {
         isUserPassCorrect(newValue) {
            const regex = /\.js$/;
            return regex.test(newValue);
         },
      },
   }
</script>

<style lang="scss" scoped>
input {
   padding: 5px 10px;
   border-radius: 6px;
   border: 1px solid #000;
   min-width: 100%;
   background-color: transparent;
}
label, input {
   font-size: 24px;
   line-height: 1.5;
   font-weight: 500;
}
label {
   display: grid;
   grid-template-columns: 0.25fr 1fr;
   align-items: center;
   column-gap: 30px;
}
.pass-incorrect {
   background-color: red;
}
</style>