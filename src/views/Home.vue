<template>
  <div>
    <AddTask v-if="showAddTask" @add-task="addTask"></AddTask>
  </div>
  <Tasks  @delete-task="deleteTask" @toggle-reminder="toggleReminder" :tasks="tasks"></Tasks>
</template>

<script>
import Tasks from "@/components/Tasks";
import AddTask from "@/components/AddTask";

export default {
  name: "Home",
  components:{
    Tasks,
    AddTask
  },
  props:{
    showAddTask: Boolean
  },
  data(){
    return{
      tasks: []
    }
  },
  methods:{

    // Fetch Data
    async fetchTasks(){
      const res = await fetch('https://randomuser.me/api/')
      const data = await res.json()
      console.dir(data)
      return data
    },

    deleteTask(id){
      //console.log('task',id);
      if(confirm('Are you sure?'))
        this.tasks = this.tasks.filter((task) => task.id !== id)
    },
    toggleReminder(id){
      this.tasks.forEach( (task) =>{
        if(task.id === id){
          task.reminder = !task.reminder
        }
      })
    },
    addTask(task){
      //this.tasks.push(task)
      this.tasks = [...this.tasks, task]
    },
  },
  created() {
    this.fetchTasks();
    this.tasks = [
      {
        id:1,
        text: 'Doctor',
        day: '23.03.2021',
        reminder: true
      },
      {
        id:2,
        text: 'Michael Meeting',
        day: '27.03.2021',
        reminder: false
      },
      {
        id:3,
        text: 'Meeting at School',
        day: '01 .04.2021',
        reminder: true
      },
    ]
  }
}
</script>

<style scoped>

</style>