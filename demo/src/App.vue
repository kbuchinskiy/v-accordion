<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <v-accordion :tab-to-open-initially="1" :horizontal="false" :one-tab-to-open="false">
      <v-accordion-tab></v-accordion-tab>
      <v-accordion-tab></v-accordion-tab>
      <v-accordion-tab></v-accordion-tab>
    </v-accordion>
  </div>
</template>

<script>
import components from '../../index.js'

export default {
  name: 'app',
  components
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
