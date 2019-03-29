/* eslint-disable */

<template>
  <li>{{ todo.text }}</li>
</template>

<script>
  export default {
    props: {
      todo: {}
    },
    name: "todo-item",

  }
</script>

<style scoped>

</style>