<template>
  <div class="block" v-if="showBlock" @click="stopTimer">Click me</div>
  <!-- EXPLANATION: We want to show the user the reaction time inside the Results component eventually. This component will be placed below the Block component in App.vue. To show the reaction time inside the Results component, we need the reactionTime data that is stored inside the Block component.In other words, we need to pass it up to the App component and then pass it down to the Results component. We can do this by emiting a custom event from the Block component.  -->
</template>

<script>
export default {
  props: ['delay'],
  data() {
    return {
      showBlock: false,
      timer: null,
      reactionTime: 0,
    };
  },

  mounted() {
    setTimeout(() => {
      this.showBlock = true;
      this.startTimer();
    }, this.delay);
  },

  methods: {
    startTimer() {
      this.timer = setInterval(() => {
        this.reactionTime += 10;
      }, 10);
    },

    stopTimer() {
      clearInterval(this.timer);
      console.log(this.reactionTime);
      // N°1) Emit custom event to pass reactionTime to App.vue. By the way, the name of the custom event here is "end", but I can call it whatever I want
      this.$emit('end', this.reactionTime);
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
