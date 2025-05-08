<!-- filepath: d:\100Project\Code\daily\M3_visscreen\src\App.vue -->
<template>
  <div id="app">
    <ChartComponent />
  </div>
</template>

<script>
import ChartComponent from './components/ChartComponent.vue';

export default {
  name: 'App',
  components: {
    ChartComponent
  }
};
</script>

<style>
html,
body {
  margin: 0;
  padding: 0;
  width: 100%;
  min-height: 100%;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  width: 100%;
  display: block;
  display: flex;
  justify-content: center;
  align-items: flex-start;
  text-align: center;
}
</style>