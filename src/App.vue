<template>
<h1>Vue Reaction Timer</h1>
<button @click="start" :disabled="isPlaying">play</button>
<Block v-if="isPlaying" :delay="delay" @end="endGame"/>
<p v-if="showResults">Reaction Time: {{ score }} ms</p>
</template>

<script>
import Block from './components/Block.vue'


export default {
  name: 'App',
  components: {
    Block
  },
  data(){
    return{
      isPlaying:false,
      delay:null,
      score:null,
      showResults:false
    }
  },
  methods:{
    start(){
     this.delay = 2000 + Math.random() * 5000
     this.isPlaying = true
     this.showResults = false
    },
    endGame(reactionTime){
      this.score = reactionTime
      this.isPlaying = false
      this.showResults = true
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
  color: #444;
  margin-top: 60px;
}
</style>
