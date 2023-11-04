<template>
   <div class="custom-input">
      <label class="custom-input__label">
         {{ title }}
      </label>
      <input 
         ref="type"
         :type="type"
         :placeholder="placeholder"
         :min="addAtrMin"
         class="custom-input__input"
         v-model="inputValue"
      >
   </div>
</template>
<script>
   export default {
      name: 'CustomInput',
      props: {
         title: {
            type: String,
         },
         placeholder: {
            type: String,
         },
         type: {
            type: String,
         },
         modelValue:{
            default: null,
         },
         modelModifiers: {
            default: () => ({})
         },
      },
      computed: {
         addAtrMin() {
            if (this.type === 'number') {
               return 1;
            } else {
               return null;
            }
         },
         inputValue: {
            get() {
               return this.modelValue
            },
            set(newValue){
               if (this.modelModifiers.isAgeValid) {
                  this.isAgeVerified(newValue)
               }
               this.$emit('update:modelValue', newValue)
            }
         },
      },
      methods: {
         isAgeVerified(newValue) {
            let userAge = parseInt(newValue)
            console.log('userAge');
            console.log(userAge);
            if (userAge<1) this.$refs.type.style.backgroundColor = 'transparent';
            else if (userAge<18) this.$refs.type.style.backgroundColor = 'red';
            else if (userAge<150) this.$refs.type.style.backgroundColor = 'green';
            else this.$refs.type.style.backgroundColor = 'transparent';
         }
      },
      watch: {
         modelValue(newValue, oldValue) {
            if(this.modelModifiers.isNoEmpty) {
               if (newValue === '') this.$refs.type.style.backgroundColor = 'red';
               else if (oldValue !== newValue) 
               this.$refs.type.style.backgroundColor = 'transparent';
            }
         }
      },
      mounted () {
         if(this.modelModifiers.isNoEmpty && !this.inputValue)
            this.$refs.type.style.backgroundColor = 'red';
      },
   }
</script>

<style lang="scss" scoped>
.custom-input {
   padding: 50px 100px;
   background-color: rgb(85, 85, 85);
   box-shadow: 0 0 10px #fff;
   border-radius: 8px;
   display: flex;
   align-items: center;
   font-size: 20px;
   gap: 20px;
   &:not(:last-child) {
      margin-bottom: 30px;
   }
// .custom-input__label

&__label {
   color: #fff;
}

// .custom-input__input

&__input {
   padding: 5px 10px;
   border-radius: 6px;
   background-color: transparent;
   border: 1px solid #fff;
   &::placeholder {
      color: #dbdbdb;
   }
}
}

</style>