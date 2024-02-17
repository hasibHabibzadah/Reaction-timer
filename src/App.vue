<template>
  <h1>Hasib Reaction Timer</h1>
  <button @click="start" :disabled="isPlaying">Play</button>

  <Block v-if="isPlaying" :delay="delay" @stop="stop"/>
  <Result v-if="showReactionTime" :score="score"/>
</template>

<script>
import Block from './components/Block-component.vue';
import Result from './components/Results.vue';
export default {
  name: 'App',
  components: {
    Block,
    Result
  },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score : null,
      showReactionTime : false
    }
  },
  methods: {
    start() {
      this.delay = 2000 + Math.random() * 5000;
      this.isPlaying = true;
      console.log(this.delay);
    },
    stop(reactionTime){
      this.score = reactionTime,
      this.isPlaying = false;
      this.showReactionTime = true;
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
