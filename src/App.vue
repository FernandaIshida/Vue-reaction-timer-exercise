<template>
  <h1>Ninja Reaction Timer</h1>
  <button @click="start" :disabled="isPlaying">Play</button>
  <Block v-if="isPlaying" :delay="delay" @end="endGame"/>
  <!--Only show Results if the game is finished/showResults is true, gives acess to score, by binding it -->
  <Results v-if="showResults" :score="score"/>
</template>

<script>
import Block from './components/Block.vue'
//Added downhere the import of "results"
import Results from './components/Results.vue'

export default {
  name: 'App',
  //Added "Results" in components
  components: { Block, Results },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResults: false
    }
  },
  methods: {
    start() {
      this.delay = 2000 + Math.random() * 5000
      this.isPlaying = true
      this.showResults = false
    },
    endGame(reactionTime) {
      this.score = reactionTime
      this.isPlaying = false  
      this.showResults = true    
        }
  }
}
</script>
<!--  Challenge
      -when the game ends, show the results component
      - output the score inside the results component -->

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
