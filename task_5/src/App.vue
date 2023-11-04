<template>
  <div class="wrapper">
    <header-component />
    <main-component 
      :list-data="filteredNotebooksList" 
      :brands-list="brandsList"
      v-model:seller ="sellerInput"
      v-model:brand = "brandInput"
    />
    <footer class="footer">footer</footer>
  </div>
</template>

<script>
import HeaderComponent from './components/HeaderComponent.vue';
import MainComponent from "./components/MainComponent/index.vue";
import { notebooksList } from './constants/5_data_notebooks.js';

export default {
  name: "App",
  components: {
    HeaderComponent,
    MainComponent
  },
  data() {
    return {
      notebooksList,
      brandsList: [],
      sellerInput: '',
      brandInput: '',
    }
  },
  computed: {
    filteredNotebooksList() {
      let currentList 
      if (this.sellerInput === '' && this.brandInput === '') {
        currentList = this.notebooksList;
      } else if (this.sellerInput !== '' && this.brandInput === '') {
        currentList = this.notebooksList.filter(item => item.seller === this.sellerInput);
      } else if ( this.brandInput !== '' && this.sellerInput === '') {
        currentList = this.notebooksList.filter(item => item.brand === this.brandInput)
      } else if ( this.brandInput !== '' && this.sellerInput !== '') {
        currentList = this.notebooksList.filter(item => item.seller === this.sellerInput && item.brand === this.brandInput);
      }
      return currentList
    }
  },
  methods: {
  },
  created () {
    this.brandsList = [...(new Set(this.notebooksList.map(item => item.brand)))]
  },
};
</script>

<style lang="scss">
@import url(../src/assets/reset.css);
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
.wrapper {
  display: flex;
  flex-direction: column;
  min-height: 100vh;
}
.footer {
  flex: 0 0 auto;
  background-color: #221f1f;
  color: rgb(240, 17, 61);
  padding: 10px 15px 20px;
}

</style>
