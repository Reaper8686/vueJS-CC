<template>
  <div id="container">
    <Home title="Task Manager" />
    <Button
      @click="toggleForm"
      :name="showForm ? 'Close' : 'ADD Task'"
      :color="showForm ? 'red' : 'green'"
    />
    <!-- <Button name="update Task" color="yellow" />
    <Button name="delete Task" color="red" /> -->
    <div v-show="showForm"><AddTask @add-task="AddTask" /></div>
    <Tasks
      @toggle-reminder="toggleReminder"
      @delete-task="deleteTask"
      :tasks="tasks"
    />
  </div>
</template>

<script>
import Home from "./components/Home.vue";
import Button from "./components/Button.vue";
import Tasks from "./components/Tasks.vue";
import AddTask from "./components/AddTask.vue";
export default {
  name: "App",
  components: {
    Home,
    Button,
    Tasks,
    AddTask,
  },

  data() {
    return {
      tasks: [],
      showForm: false,
    };
  },

  methods: {
    AddTask(task) {
      this.tasks = [...this.tasks, task];
    },

    deleteTask(id) {
      this.tasks = this.tasks.filter((task) => {
        return task.id !== id;
      });
    },
    toggleReminder(id) {
      this.tasks.forEach((task) => {
        if (task.id == id) {
          task.reminder = !task.reminder;
        }
      });
    },

    toggleForm() {
      this.showForm = !this.showForm;
    },
  },

  created() {
    this.tasks = [
      {
        id: "1",
        text: "Doctors Appointment",
        day: "March 5th at 2:30pm",
        reminder: true,
      },
      {
        id: "2",
        text: "Meeting with boss",
        day: "March 6th at 1:30pm",
        reminder: true,
      },
      {
        id: "3",
        text: "Food shopping",
        day: "March 7th at 2:00pm",
        reminder: false,
      },
    ];
  },
};
</script>

<style>
#container {
  padding: 20px;
  /* border: solid black 2px;X */
}
</style>
