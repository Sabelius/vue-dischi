<template>
  <div id="app">
    <Header />
    <Discs />
  </div>
</template>

<script>
import Discs from './components/Discs.vue';
import Header from './components/Header.vue';

export default {
  name: 'App',
  components: {
    Discs,
    Header,
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
  padding-top: 60px;
}
</style>
