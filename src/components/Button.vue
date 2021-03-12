<template>
  <!-- v-on:click="" or @Click="" -->
  <button @click="onClick()"  :style="{background: color}" class="btn">{{ text }}</button>
</template>

<script>
export default {
  name: "Button",
  props: {
    text: String,
    color: String
  },
  methods: {
    onClick() {
      console.log("Hello ")
    }
  }
}
</script>

<style scoped>

</style>