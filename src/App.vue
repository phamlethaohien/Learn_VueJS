<template>
  <div id="app">
    <h4 class="bg-primary text-white text-center p-2">
      <span v-html="icon"></span>
      {{ app_name }}
    </h4>
    <div class="container p-4 text-center">
      <form class="row justify-content-center mb-4" @submit.prevent="add()">
        <input
          type="text"
          v-model="img_link"
          class="col-4 form-control"
          placeholder="Input image link"
        />
        <input
          type="text"
          v-model="task_name"
          class="col-4 form-control"
          placeholder="Input task name"
        />
        <input type="submit" class="btn btn-success" value="Add new task" />
      </form>

      <div class="row">
        <div class="col-1 font-weight-bold">No.</div>
        <div class="col-2 col-md-1 font-weight-bold">Image</div>
        <div class="col-4 font-weight-bold">Task</div>
        <div class="col-2 font-weight-bold">Done</div>
      </div>
      <div v-for="(task, index) in tasks" v-bind:key="index">
        <div class="row" v-if="!task.done">
          <div class="col-1 align-self-center">{{ index + 1 }}</div>
          <img
            class="col-2 col-md-1 img-fluid"
            src="https://pbs.twimg.com/profile_images/1245425709666816000/gkb8QvTW.jpg"
          />
          <div class="col-4 align-self-center text-left">{{ task.action }}</div>
          <div class="col-2 align-self-center text-center">{{ task.done }}</div>
          <div class="col-2 font-weight-bold">Control</div>
        </div>
      </div>
      <div v-for="(task, index) in tasks" v-bind:key="index">
        <div class="row" v-show="task.done">
          <div class="col-1 align-self-center">{{ index + 1 }}</div>
          <img class="col-2 col-md-1 img-fluid" v-bind:src="task.image_link" />
          <div class="col-4 align-self-center text-left">{{ task.action }}</div>
          <div class="col-2 align-self-center text-center">{{ task.done }}</div>
          <div class="col-2 align-self-center text-center">
            <input
              type="checkbox"
              v-model="task.done"
              class="form-check-input"
            />
            {{ task.done }}
            <div class="col-2 align-self-center">
              <button class="btn btn-danger" v-on:click="remove(index)">
                <i class="fa fa-trash" aria-hidden="true"></i>
              </button>
            </div>
          </div>
        </div>
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
        {
          action: "Buy Flowers",
          image_link:
            "https://i.pinimg.com/originals/09/2f/d0/092fd0a6692251c33744c77697c9b544.png",
          done: false,
        },
        {
          action: "Get Shoes",
          image_link:
            "https://www.freeiconspng.com/thumbs/tasks-icon/tasks-icon-9.png",
          done: false,
        },
        {
          action: "Collect Tickets",
          image_link:
            "https://pbs.twimg.com/profile_images/1245425709666816000/gkb8QvTW.jpg",
          done: true,
        },
        {
          action: "Call Joe",
          image_link:
            "https://iconarchive.com/download/i75526/cornmanthe3rd/squareplex/Utilities-tasks.ico",
          done: false,
        },
      ],
      task_name: "",
      img_link: "",
    };
  },
  methods: {
        add() {
          if (this.task_name !== "")
            this.tasks.push({
              action: this.task_name,
              image_link: this.img_link,
              done: false,
            });
          else alert("You have to input content");
        },
        remove(index) {
          this.tasks.splice(index, 1);
        },
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
