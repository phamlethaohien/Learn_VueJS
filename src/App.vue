<template>
  <div id="app">
    <h4 class="bg-primary text-white text-center p-2">
      <span v-html="icon"></span>
      {{ app_name }}
    </h4>
    <div class="container p-4 text-center">
      <div class="row">
        <div class="col-1 font-weight-bold">No.</div>
        <div class="col-2 col-md-1 font-weight-bold">Image</div>
        <div class="col-4 font-weight-bold">Task</div>
        <div class="col-2 font-weight-bold">Done</div>
      </div>
      <div class="row" v-for="(task, index) in tasks" v-bind:key="index">
        <div class="col-1 align-self-center">{{ index + 1 }}</div>
        <img class="col-2 col-md-1 img-fluid" src="https://pbs.twimg.com/profile_images/1245425709666816000/gkb8QvTW.jpg"/>
        <div class="col-4 align-self-center text-left">{{ task.action }}</div>
        <div class="col-2 align-self-center text-center">{{ task.done }}</div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  el: "#app",
  data() {
    return {
      app_name: "To do list",
      icon: '<i class="fa fa-calendar" aria-hidden="true"></i>',
      tasks: [
        { action: "Buy Flowers", image_link: "", done: false },
        { action: "Get Shoes", image_link: "", done: false },
        { action: "Collect Tickets", image_link: "", done: true },
        { action: "Call Joe", image_link: "", done: false },
      ],
    };
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
</style>
