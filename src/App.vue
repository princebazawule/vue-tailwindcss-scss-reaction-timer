<template>
  <h1 class="text-4xl font-extrabold">Reaction Timer</h1>
  <button 
    class="my-8 ring-4 text-2xl py-3 px-8 rounded-lg"
    :class="isPlaying ? 'opacity-50 cursor-not-allowed' : ''"
    @click="start" 
    :disabled="isPlaying"
  >play</button>
  
  <Block v-if="isPlaying" :delay="delay" @end="endGame" />
  <Results v-if="showResults" :score="score" />
</template>

<script>
import Block from './components/Block.vue'
import Results from './components/Results.vue'

export default {
  name: 'App',
  components: {
    Results,
    Block
  },
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
      this.isPlaying = true
      this.delay = 1000 + Math.random() * 2000
      this.showResults = false,
      this.score = null
    },
    endGame(reactionTime) {
      this.score = reactionTime
      this.isPlaying = false,
      this.showResults = true
    }
  },
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
