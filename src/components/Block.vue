<template>
  <div class="block" v-if="showBlock">Click me</div>
</template>

<script>
export default {
  props: ['delay'],
  data() {
    return {
      showBlock: false,
    };
  },

  mounted() {
    setTimeout(() => {
      this.showBlock = true;
    }, this.delay);
  },

  updated() {
    console.log(
      `the variable updated is showBlock, which now has a value of ${this.showBlock}`
    );
  },

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
