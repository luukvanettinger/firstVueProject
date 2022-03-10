<script>
import Header from './components/Header.vue'
import Tasks from './components/Tasks.vue'
import AddTask from './components/AddTask.vue'

export default {
  name: "App",
  components: {
    Header,
    Tasks,
    AddTask,
  },
  data() {
    return {
      tasks: [],
      showAddTask: false,
    }
  },
  methods: {
    toggleAddTask() {
      this.showAddTask = !this.showAddTask
    },
    addTask(task) {
      this.tasks = [...this.tasks, task]
    },
    deleteTask(id) {
      if(confirm('u sure bro?')){
        this.tasks = this.tasks.filter((task) => task.id !== id)
      }
    },
    toggleReminder(id) {
      this.tasks = this.tasks.map((task) => task.id === id ? {...task, reminder: !task.reminder} : task)
    }
  },
  created() {
    this.tasks = [
      {
        id: 1,
        text: 'Eat my guacamole 🥑',
        day: 'March 11th at 2:30pm',
        reminder: true,
      },
      {
        id: 2,
        text: 'Go to the gym 💪',
        day: 'March 11th at 4:30pm',
        reminder: true,
      },
      {
        id: 3,
        text: 'Hug Jerry ❤️',
        day: 'March 12th at 1:00pm',
        reminder: false,
      },
    ]
  }
}
</script>


<template>
  <div class="container">
      <Header
        :showAddTask="showAddTask"
        @toggle-add-task="toggleAddTask" 
        title="Luuk's Task Tracker 😎" />
      <div v-if="showAddTask"> 
        <AddTask @add-task="addTask" />
      </div>
      <Tasks 
        @toggle-reminder="toggleReminder"
        @delete-task="deleteTask" 
        :tasks="tasks" 
      />
  </div>
</template>


<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
body {
  font-family: 'Poppins', sans-serif;
}
.container {
  max-width: 500px;
  margin: 30% auto;
  overflow: auto;
  min-height: 300px;
  padding: 30px;
  border-radius: 5px;
  margin-top: -30px;
}
.btn {
  display: inline-block;
  background: #000;
  color: #fff;
  border: none;
  padding: 10px 20px;
  margin: 5px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
}
.btn:focus {
  outline: none;
}
.btn:active {
  transform: scale(0.98);
}
.btn-block {
  width: 100%;
}
</style>
