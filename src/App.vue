<template>
  <div id="app">
    <carousel :items="items" />
  </div>
</template>

<script>
import Carousel from "./components/Carousel";

export default {
  name: "App",
  
  data() {
    return {
      items: [{
        text: 'alo ha',
      }, {
        text: 'alo ha 111',
      }, {
        text: 'alo ha 222',
      }, {
        text: 'alo ha 333',
      }, {
        text: 'alo ha 444',
      }, {
        text: 'alo ha 555',
      }, {
        text: 'alo ha 666',
      }, {
        text: 'alo ha 777',
      }],
    };
  },

  components: {
    Carousel
  }
};
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
