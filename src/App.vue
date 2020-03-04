<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <!-- <HelloWorld msg= "shitty hell"/> -->
    <what msg="message in the prop"/>
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import what from './components/NewComponent.vue'
export default {
  name: 'App',
  components: {
    // HelloWorld,
    what
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
