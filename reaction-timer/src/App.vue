<template>
<h1>Reaction Timer Game</h1>
<button @click="start" :disabled="isPlaying">Play</button>
<Block v-if="isPlaying" :delay="delay" @end="endGame" />
<Results v-if="showResults" :score="score" />
</template>

<script>
import Block from './components/Block.vue'
import Results from './components/Results.vue'

export default {
  name: 'App',
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

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #444;
  margin-top: 60px;
}

#app:after {
    content : "";
    display: block;
    position: absolute;
    top: 0;
    left: 0;
    background-image: url('https://images.unsplash.com/photo-1606178576347-f0f6cf180ecf?ixid=MXwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHw%3D&ixlib=rb-1.2.1&auto=format&fit=crop&w=891&q=80');
    background-repeat: none;
    background-size: cover;
    background-position: center;
    width: 100%;
    height: 100%;
    opacity : 0.7;
    z-index: -1;
}

button{
  margin: 10px;
  padding: 8px 16px;
  background-color: #4e8d7c;
  color: #fff;
  border: none;
  font-size: 16px;
  letter-spacing: 1px;
  cursor: pointer;
  border-radius: 4px;;
}

button:focus {
  outline: none;
}

button:active {
  transform: scale(.98);
}

button[disabled] {
  opacity: .2;
  cursor: not-allowed;
}
</style>
