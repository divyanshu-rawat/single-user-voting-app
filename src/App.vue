<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/wow.png">
    <HelloWorld msg="Welcome to the Voting Application"/>
    <div>
      <ul>
        <li v-for="(framework, index) in frameworks" :key='index' >

        {{framework.name}} has - {{framework.votes}} votes

        <button v-on:click = "voteFor(framework)">UpVote</button>
        <button v-on:click = "remove(framework)" v-if = "editMode">Delete</button>

      </li>
      </ul>

      <button v-on:click = "toggleEditMode" >{{editMode ? 'Done' : 'Edit' }}</button>
      
      <div class="margin">
        <input v-if="editMode" placeholder="Add new Framework" v-on:keyup.enter="addNew">
      </div>

      <p class="margin">Current Winner(s): {{winnerString}}</p>

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
      editMode: false,
      frameworks: [
        { name: 'Vue.js', votes: 0 },
        { name: 'React', votes: 0 },
        { name: 'Angular', votes: 0 }
    ]
    }
  },
  methods: {
       voteFor: function(f) {
          f.votes += 1;
          this.computecurrentWinner()
        },
        addNew: function (e) {
          this.frameworks.push(
            {name: e.target.value, votes: 0}
          )
          e.target.value = '';
          this.save();
        },
        remove: function (f) {
          this.frameworks = this.frameworks.filter( x => x != f)
          this.save();
        },
        load: function() {

           let data = localStorage.getItem('saved');
            if (data) {
              this.frameworks = JSON.parse(data)
            }
          },
         save: function() {
            let data = JSON.stringify(this.frameworks)
            localStorage.setItem('saved', data)
          },

         toggleEditMode: function() {
            this.editMode = !this.editMode
          }
    },
      computed: {
        winnerString: function() {
          let scores = this.frameworks.map(f => f.votes)
          let highscore = Math.max.apply(Math, scores)
          let bestList = this.frameworks.filter(f => f.votes == highscore)

          let bestNames = bestList.map(f => f.name)
          return bestNames.join(', ')
        }
      },

     created: function() {
       this.load();
    }
}



</script>

<style>

* { color: inherit; }

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

#margin{
  margin-top: 5px;
}


input { text-align: center; }

img {
  width: 8rem; height: 8rem;
  vertical-align: calc(-0.12109375em);
}

</style>
