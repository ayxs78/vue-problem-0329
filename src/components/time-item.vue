<template>
  <div>
    <p>现在是:</p>
    <p>{{date}}</p>
  </div>
</template>

<script>
  export default {
    name: "time-item",
    data: function () {
      return {
        date: new Date().toLocaleTimeString()
      }
    },
    methods: {
      updateDate: function () {
        this.date = new Date().toLocaleTimeString();
      }
    },
    created() {
      setInterval(this.updateDate, 1000);
    }

  }
</script>

<style scoped>

</style>