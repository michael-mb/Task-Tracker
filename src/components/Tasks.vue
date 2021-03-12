<template>
  <div :key="task.id" v-for="task in tasks">
    <!-- Emit me sert a passer les infos d'un component à celui qui l'utilise -->
    <Task @delete-task="$emit('delete-task',task.id)" :task="task"></Task>
  </div>
</template>

<script>
import Task from "@/components/Task";

export default {

  name: "Tasks",
  props:{
    tasks: Array
  },
  components:{
    Task
  },
  emits: ['delete-task']
}
</script>

<style scoped>

</style>