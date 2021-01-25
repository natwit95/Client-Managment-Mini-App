<template>
<div id="app">
  <ClientsList v-bind:clients="clients"/>
</div>

</template>

<script>
import axios from "axios";
import ClientsList from "./components/ClientsList"

export default {
  name: 'App',
  components: {
    ClientsList
  },
  data() {
    return {
      clients: []
    }
  }, 
  methods: {
    created() {
      axios.get('https://jsonplaceholder.typicode.com/users?')
      .then(resp => this.clients = resp.data)
      .catch(err => console.log(err))
    }
  }
  
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
