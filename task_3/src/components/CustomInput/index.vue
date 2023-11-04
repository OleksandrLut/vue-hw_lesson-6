<template>
   <div class="custom-input">
      <input
         placeholder="Введіть email"
         type="text"
         v-model.lazy="userEmail"
         :style="{ backgroundColor: inputBgColor }"
      />
   </div>
</template>

<script>
   export default {
      name: "CustomInput",
      props: {
         modelValue: {
            type: String,
         },
         modelModifiers: {
            default: () => ({})
         },
      },
      data() {
         return {
            inputBgColor: null,
            existingEmails: [
               "ivanov_ivan@inv.mn.edu",
               "petrov_prto@inv.mn.edu",
               "romanov@inv.mn.edu",
               "vasya@inv.mn.edu",
               "victor@inv.mn.edu", 
            ],
         };
      },
      computed: {
         userEmail: {
            get() {
               return this.modelValue;
            },
            set(newValue) {
               let emailVal = newValue.includes("@inv.mn.edu")
                  ? newValue
                  : this.addPostfix(newValue);
               if (this.modelModifiers.check) this.isExistEmail(emailVal);
               this.$emit("update:modelValue", emailVal);
            },
         },
      },
      methods: {
         addPostfix(val) {
            return val.includes("@inv.mn.edu") ? val : val + "@inv.mn.edu";
         },
         isExistEmail(emailVal) {
            if (this.existingEmails.includes(emailVal)) {
               this.inputBgColor = "green";
            } else {
               this.inputBgColor = "red";
            }
         },
      },
   };
</script>

<style scoped>
   .custom-input {
      padding: 30px 150px;
      box-shadow: 0 0 8px rgb(100, 99, 99);
      border-radius: 8px;
   }
   .custom-input input {
      padding: 5px 10px;
      border-radius: 6px;
      background-color: rgb(100, 99, 99);
      box-shadow: 0 0 10px rgb(247, 255, 135);
      font-size: 20px;
      min-width: 400px;
      color: #fff;
   }
   .custom-input input::placeholder {
      color: rgb(247, 255, 135);
      font-size: 20px;
      text-align: center;
   }
</style>