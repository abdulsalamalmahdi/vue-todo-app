<template>
  <div id="demo">
    <h1 v-if="msg">{{ msg }}</h1>
    <h1 v-else>no message in here</h1>
    <button v-on:click="toggle">
    Toggle
  </button>
  <transition name="fade">
    <p v-if="show"><img src="../assets/logo.png" alt="logo" title="logo"></p>
  </transition>
    
  </div>
</template>

<script>
export default {
  name: 'what',
  data(){
    return {show: false}
  },
  props: {
    msg: String
  },
  methods:{
    toggle(){
     
      return this.show= !this.show;
    },
  }
  
}

  
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
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
img{
  width: 30%;
  height: 30%;
}
.fade-enter-active, .fade-leave-active {
  transition: opacity 1s;
}
.fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0;
}
</style>
