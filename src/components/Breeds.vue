<template>
  <div class="sample">
    <b-card
      :title="breed.name"
      :sub-title="breed.temperament"
      class="m-2"
    >
      <b-card-text>
        {{ breed.description }}
      </b-card-text>
      <b-link :href="breed.wikipedia_url" target="_blank">Wikipedia</b-link>
      <!-- {{ breed}} -->
    </b-card>
  </div>
</template>

<script>

export default {
  name: 'Sample',
  props: {
    breed: Object
  },
}
</script>

<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}

a:hover {
  color: #42b983;
  text-decoration: none;
}

.card {
  max-width: 350px;
  height: 450px;
}
</style>
