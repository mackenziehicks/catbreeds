<template>
  <div id="app" class="container my-5">
    <div class="text-center mb-4">
      <img alt="Vue logo" src="./assets/logo.png">
      <h1 class="text-center mb-0">Cat Breeds</h1>
    </div>
    <div
      v-if="error"
      class="text-center"
    >
      <p class="text-danger">{{ error }}</p>
    </div>
    <div class="d-flex flex-wrap justify-content-center">
      <Breeds 
        v-for="breed in breeds" 
        :key="breed.id"
        :breed="breed"
      />
    </div>
    
  </div>
</template>

<script>
import Breeds from './components/Breeds.vue'
import axios from 'axios';

export default {
  name: 'App',
  components: {
    Breeds
  },
  data() {
    return {
      breeds: null,
      error: null
    }
  },
  mounted() {
    axios
      .get('https://api.thecatapi.com/v1/breeds', {'x-api-key': '7ccb244e-75cc-48ac-8814-43da01bc1470'})
      .then(response => {
        this.error = null;
        this.breeds = response.data;
      })
      .catch(error => {
        this.error = error;
        console.log(error);
      });
  }
}
</script>

<style scoped>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
