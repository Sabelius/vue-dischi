<template>
  <div id="app">
    <Discs />
  </div>
</template>

<script>
import Discs from './components/Discs.vue';

export default {
  name: 'App',
  components: {
    Discs,
  },
}
</script>

<style lang="scss">
@import "./style/general.scss";

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
