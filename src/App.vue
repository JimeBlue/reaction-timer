<template>
  <h1>Ninja Reaction Timer</h1>
  <button @click="start" :disabled="isPlaying">play</button>
  <!-- N° 2) React/receive custom event "end" sent from Block, which contians the variable reactionTime. We receive the "end" custom event and set it to the function endGame(), which will run when the event occurrs-->
  <Block v-if="isPlaying" :delay="delay" @end="endGame" />
  <!-- N°5) Ouput the reaction time to the user, now stored in the variable score, for now here in. Eventually, it will be shown in the Results component -->
  <!-- N°7) Only show the reaction time if showResults is true -->
  <p v-if="showResults">Reaction Time {{ score }} ms</p>
</template>

<script>
import Block from './components/Block';
export default {
  name: 'App',
  components: { Block },
  data() {
    return {
      isPlaying: false,
      delay: null,
      // N°4) Create the variable score to store the value of the reactionTime variable passed by the Block component. initially is null
      score: null,
      // N°6) Create variable that will be conditionally used to show the results only when the game is over.
      showResults: false,
    };
  },
  methods: {
    start() {
      this.delay = 2000 + Math.random() * 5000;
      this.isPlaying = true;
      // N°9) Set showResults to false again so that the reaction time is not seen when I click start again
      this.showResults = false;
    },
    // N°3) This function runs when the custom event "end" occurrs. This means that this function basically receives the variable reactionTime passed by the Block component throught the custom event "end". Inside this function I put reactionTime inside the score variable that I created in step n°4. I also want to set isPlaying back to false to stop the game
    endGame(reactionTime) {
      this.score = reactionTime;
      this.isPlaying = false;
      // N°8) Here at the end of the game set showResults to true so that the reaction time can be shown to the user
      this.showResults = true;
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
