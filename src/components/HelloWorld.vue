<template>
  <div class="hello">
    <h2 class="todolist-heading">{{vInfo}}</h2>
    <TodoList v-bind:todos="todos" @input-click="inputClicked"/>
  </div>
</template>

<script>
import TodoList from "./TodoList.vue"
export default {
  name: 'HelloWorld',
  components: {
  TodoList
  },
  props: {
    vInfo: String,
    todos: Array
  },
  methods: {
    inputClicked(value) {
      this.$emit("againClickCalled", value)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
.todolist-heading {
  font-weight: bold;
  font-size: 40px;
  text-decoration: underline
}
</style>


//<TodoList v-bind:todos="todos" v-on:input-click="$emit('clickedInput', value)"/> ..... here the value will be undefined will not update auto.
//<TodoList v-bind:todos="todos" v-on:input-click="inputClicked"/>

//$emit cannot be converted to v-on and @ or vice-versa
//$emit used when sending emit event to the another component with params or not.
// when we received the event than we have to again pass the params it will not attach auto IN CASE WE AGAIN SENDING EVENT TO ANOTHER COMPONENT.

// we can accept the mouse events fromm where its origin from.... it will attach to that particular component..
