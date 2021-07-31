<template>
  <div class="container">
    <h1>NoteBook</h1>
    <Header
        :showAddTask="showAddTask"
        @toggle-add-task="toggleAddTask"
    />
    <div v-if="showAddTask">
      <AddTask
          @add-task="addTask"
      />
    </div>

    <Tasks
        @toggle-reminder="toggleReminder"
        @delete-task="deleteTask"
        :tasks="tasks"/>
    <h6>Made by jalbeh@icloud.com</h6>
  </div>

</template>

<script>
import Header from "./components/Header";
import Tasks from "./components/Tasks";
import AddTask from "./components/AddTask";

export default  {
  name: "App",
  components: {AddTask, Tasks, Header},
  data() {
    return {
      tasks: [],
      showAddTask: false
    }
  },
  methods: {
    toggleAddTask() {
      this.showAddTask = !this.showAddTask
    },
    addTask(task){
      this.tasks = [...this.tasks, task]
    },
    deleteTask(id) {
      if(confirm("Are you sure?")) {
        this.tasks = this.tasks.filter((task) => task.id !== id)
      }
    },
    toggleReminder(id) {
      console.log(id)
      this.tasks = this.tasks.map((task) => task.id === id ? {...task, reminder: !task.reminder} : task)

    }
  },
  created() {
    this.tasks = [
      {
        id: 1,
        text: 'Hello world',
        day: 'July 31',
        reminder: false
      },
      {
        id: 2,
        text: 'Apple',
        day: 'July 31',
        reminder: true
      },
      {
        id: 3,
        text: 'Coca Cola',
        day: 'July 31',
        reminder: true
      }
    ]
  }
}
</script>

<style>

  *{
    box-sizing: border-box;
    padding: 0;
    margin: 0;
  }
  body {
    font-family: "Poppins", sans-serif;
  }
  .container {
    max-width: 500px;
    margin: 30px auto;
    overflow: auto;
    min-height: 300px;
    border: 1px solid steelblue;
    padding: 30px;
    border-radius: 5px;
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
    display: block;
    width: 100%;
  }
</style>
