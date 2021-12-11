<template>
  <div id="app">
    <h4 class="bg-primary text-white text-center p-2">
      <span v-html="icon"></span>
      {{ app_name }}
    </h4>
  </div>
</template>

<script>

export default {
  name: 'App',
  el: '#app',
  data() {
    return {
      app_name: 'To do list',
      icon: '<i class="fa fa-calendar" aria-hidden="true"></i>'
    };
  },
}
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
