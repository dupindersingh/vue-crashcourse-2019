<template>
  <div class="vue-info">
    <p>This party is coming from VueInfo component.</p>
    <h1>{{title}}</h1>
  </div>
</template>

<script>
export default {
  name: "VueInfo",
  props: {
    title: String
  },
}
</script>

<style>
  .vue-info {
    background-color: seagreen;
    padding: 10px;
    color: white
  }
</style>
