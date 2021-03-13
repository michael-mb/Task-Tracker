<template>
  <header>
    <h1>{{title}}</h1>
    <!-- Quand tu mets les : ca veut dire que tu veux use les variables  -->
    <Button v-show="homePage" @toggle-form="$emit('toggle-form')" :text="showAddTask ? 'Close' : 'Add Task' " :color="showAddTask ? 'red' : 'green'" :showAddTask="showAddTask"></Button>
  </header>
</template>

<script>
import Button from "@/components/Button";

export default {
  name: "Header",
  props: {
    title: {
      type: String,
      default: 'Hello World'
    },
    showAddTask : {
      type: Boolean,
    },
  },
  components:{
    Button
  },
  computed:{
    homePage(){
      return this.$route.path === '/';
    }
  },
  emits: ['toggle-form']
}
</script>

<style scoped>
  header{
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 20px;
  }
</style>