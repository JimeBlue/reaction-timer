<template>
  <h1>Ninja Reaction Timer</h1>
  <!-- on click call the function start -->
  <button @click="start">play</button>
  <Block v-if="isPlaying" />
</template>

<script>
import Block from './components/Block';
export default {
  name: 'App',
  components: { Block },
  data() {
    return {
      // By default is false, it changes to true when the play btn is clicked
      isPlaying: false,
      //The amount of time there´s going to be before Block appears on the screen
      delay: null,
    };
  },
  methods: {
    // On click this function updates delay to something between 2 and 4 seconds and sets isPlaying to true
    start() {
      this.delay = 2000 + Math.random() * 5000;
      this.isPlaying = true;
      console.log(this.delay);
    },
  },
};
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
