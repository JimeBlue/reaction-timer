<template>
  <!-- N°7) Call stopTimer() on click  -->
  <div class="block" v-if="showBlock" @click="stopTimer">Click me</div>
  <!-- EXPLANATION: The problem:  meassure the user´s reaction time. I.e the time between the green square appears on the screen and the clicking of the square.-->
</template>

<script>
export default {
  props: ['delay'],
  data() {
    return {
      showBlock: false,
      // N° 4) Create the timer variable to store a set interval, which is going to run every 10 milliseconds. initially is given the value null
      timer: null,
      reactionTime: 0,
    };
  },

  mounted() {
    setTimeout(() => {
      this.showBlock = true;
      // N° 3)Call Create startTimer()
      this.startTimer();
    }, this.delay);
  },
  // N° 1) Create startTimer() method to start the timer when the green box appears on the screen. I need to call this method as soon as the green square box appears on the screen, therfore, I call it inside the setTimeout() method above.
  // N° 2) Create stopTimer() method to stop the timer when the user clicks on the green box
  methods: {
    // N°5) Here we set the variable timer to run the setInterval function every 10 milliseconds. And every 10 milliseconds we are going to increase the variable reactionTime by 10 milliseconds. So the timer is running in 10 milliseconds steps until we stop the timer.
    startTimer() {
      this.timer = setInterval(() => {
        this.reactionTime += 10;
      }, 10);
    },
    // N°6) When we stop the timer we want to clear the interval. When we clear the interval, the function setInterval() is not longer going to fire, so reaction time is no longer going to increase. Finally, we want to call the clearInterval () function when the user clicks on the green box, which is in the <div class="block"> above.
    stopTimer() {
      clearInterval(this.timer);
      console.log(this.reactionTime);
    },
  },
};
</script>

<style>
.block {
  width: 400px;
  border-radius: 20px;
  background: #0faf87;
  color: white;
  text-align: center;
  padding: 100px 0;
  margin: 40px auto;
}
</style>
