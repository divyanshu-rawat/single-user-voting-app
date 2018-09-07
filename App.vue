<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/wow.png">
    <HelloWorld msg="Welcome to Your Vue.js Application"/>
    <div class="">A custom component! {{name}}</div>
  </div>

</template>

<script>
import HelloWorld from './components/HelloWorld.vue'


export default {
  name: 'app',
  components: {
    HelloWorld
  },
  data(){
    return {
      name : 'divyanshu'
    }
  }
}



</script>

<style>

* { color: inherit; }

input { font: inherit; border: unset; background: unset; }
input:focus { outline: unset; }

:root {
  font: 1rem/1.175 "BlinkMacSystemFont", -apple-system, "Roboto", sans-seri;
}


#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}


input { text-align: center; }

img {
  width: 8rem; height: 8rem;
  vertical-align: calc(-0.12109375em);
}

</style>
