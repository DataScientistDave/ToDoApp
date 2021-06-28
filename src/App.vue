<template>
  <div>
    <Header />
    <div class="tasks-app">
      <AddTask @add-task = "addTask" />
      <Tasks :tasks = "tasks" @delete-task = "deleteTask"
      @complete-task = "completeTask" @add-task = "addTask"/>
    </div>
  </div>
</template>

<script>

import Header from './components/Header'
import AddTask from './components/AddTask'
import Tasks from './components/Tasks'

export default {
  name: 'App',
  components: {
    Header,
    AddTask,
    Tasks,
  },
  data() {
    return {
      tasks: []
    }
  },
  created() {
    this.tasks = [
      {
        id: 1,
        text: "Wash Dishes",
        completed: false
      },
      {
        id:2,
        text: "Doctor's Appointment",
        completed: false
      },
      {
        id:3,
        text: "Do Homework",
        completed: false
      },
    ]
  },
  methods : {
    addTask(task) {
      this.tasks = [... this.tasks,task];
    },
    deleteTask(id) {
      this.tasks = this.tasks.filter(task => task.id !== id);
    },
    completeTask(id) {
      const completedTask = this.tasks.find(task => task.id === id);
      completedTask.completed = true;
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  display: flex;
  align-items:center;
  justify-content: center;
  padding-left: 75px;
}
body {
    background: linear-gradient(
    45deg,
    rgb(240, 137, 2) 25%,
    rgb(197, 95, 95) 100%
  );
}
.tasks-app {
  display: flex;
  flex-direction: column;
  justify-content: start;
  width: 520px;
  min-height: 600px;
  background: #0b0142;
  text-align: center;
  margin: 128px auto;
  border-radius: 10px;
  padding-bottom: 32px;
  padding-top: 20px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, .12)
}
</style>
