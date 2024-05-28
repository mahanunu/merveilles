<template>
  <div id="app">
    <Wonders />
  </div>
</template>

<script>
import Wonders from './components/Wonders.vue';

export default {
  name: 'App',
  components: {
    Wonders
  }
};
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap');

body {
  font-family: 'Roboto', sans-serif;
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  background-color: #64C9CF;
}

#app {
  text-align: center;
  color: #DF711B;
  margin-top: 60px;
}
</style>
