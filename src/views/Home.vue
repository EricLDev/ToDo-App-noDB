<template>
  <AddTask v-show="showAddTask" @add-task="addTask" />
  <Tasks
    @toggle-reminder="toggleReminder"
    @delete-task="deleteTask"
    :tasks="tasks"
  />

</template>

<script>
import Tasks from "../components/Tasks";
import AddTask from "../components/AddTask";

export default {
  name: "Home",
  props: {
    showAddTask: Boolean,
  },
  components: {
    Tasks,
    AddTask,
  },
  data() {
    return {
      tasks: [],
    };
  },
  created (){
    this.tasks = [
    {
      "id": 1,
      "text": "Doctors Appointment",
      "day": "2021-06-23",
      "time": "10.00am",
      "reminder": true
    },
    {
      "id": 2,
      "text": "Meeting with boss",
      "day": "2021-07-02",
      "time": "1.30pm",
      "reminder": true
    },
    {
      "id": 3,
      "text": "Grocery Shopping",
      "day": "2021-06-25",
      "time": "5.00pm",
      "reminder": false
    },

    ];
  },
  methods: {
    addTask(task){
      this.tasks = [...this.tasks, task]
    },

    deleteTask(id){
      if(confirm('Are you sure?')){
        this.tasks = this.tasks.filter((task) => task.id !== id )
      }
    },

    toggleReminder(id){
      this.tasks = this.tasks.map((task) => task.id === id ? {...task, reminder: !task.reminder} : task)
    },
    toggleAddTask() {
      this.showAddTask = !this.showAddTask;
    },
  },
}
</script>

<style>
</style>