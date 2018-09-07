<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/wow.png">
    <HelloWorld msg="Welcome to the Voting Application"/>
    <div>
      <ul>
        <li v-for="(framework, index) in frameworks" :key='index' >

        {{framework.name}} has - {{framework.votes}} votes

        <button v-on:click = "voteFor(framework)">UpVote</button>

      </li>
      </ul>
    </div>

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
      name : 'divyanshu',
      frameworks: [
        { name: 'Vue.js', votes: 0 },
        { name: 'React', votes: 0 },
        { name: 'Angular', votes: 0 }
    ]
    }
  },
  methods: {
       voteFor: function(f) {
          f.votes += 1
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
  color: #2c3e50;
  margin-top: 60px;
}


input { text-align: center; }

img {
  width: 8rem; height: 8rem;
  vertical-align: calc(-0.12109375em);
}

</style>
