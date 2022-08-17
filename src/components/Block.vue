<template>
  <div class="block" v-if="showBlock">Click me</div>
  <!-- EXPLANATION: Problem: I want this module to appear in the screen only after a randomly created delay. The solution is given with number steps.  -->
</template>

<script>
export default {
  // N°1) We accept the prop delay, which we created in App.vue and which contains a random delay
  // N°2) We create the variable "showBlock" and set it to false. And in the template, we say only show the block if "showBlock" is true (v-if="showBlock).
  props: ['delay'],
  data() {
    return {
      showBlock: false,
    };
  },

  // N°3) When the component mounts, we start a timer with the method setTimeout(), which will fire some code after an amount of time, in this case we use our variable delay for the amount of time. So, after that amount of time, set  "showBlock" to be true. In this way, we make the block to appear on the screen after a random amount of time.
  mounted() {
    setTimeout(() => {
      this.showBlock = true;
    }, this.delay);
  },
  //EXPLANATION: The updated hook fires when any data inside the component is updated. After the setTimeout methods fires in the mounted hooked, the "showBlock" function changes to true and therefore it is updated. In the updated hooked we can see that. If I want to do something we data that is updated, I have to do it here.
  updated() {
    console.log(
      `the variable updated is showBlock, which now has a value of ${this.showBlock}`
    );
  },
  // EXPLANATION: the unmounted hook fires when a component is unmounted from the dom, i.e when we don´t see it anymore. Here the component is not unmounted, but if I go to App.vue and comment out the Block component, I will see console.log below. The unmounted hook is used when Vue router when we go from page to page. When we navigate away from a page, the component of that page will unmount.
  unmounted() {
    console.log('The Block component has been unmounted');
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
