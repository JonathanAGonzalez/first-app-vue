<template>
  <!-- <img alt="Vue logo" src="./assets/logo.png" /> -->
  <!-- <Counter title="Counter" :start="10" /> -->
  <Indecision />
</template>

<script>
import Counter from './components/Counter.vue';
import HelloWorld from './components/HelloWorld.vue';
import Indecision from './components/Indecision.vue';

export default {
  name: 'App',
  components: {
    Counter,
    HelloWorld,
    Indecision,
  },
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
body {
  background: #222;
}
</style>
