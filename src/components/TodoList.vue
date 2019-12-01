<template>
<div>
<form @submit="handleSubmit">
<input type="text" v-model="todoName" v-on:change="changeTodoName(e.target.value)" v-on:click="$emit('input-click', $event.target.value)"/>
<button>Add Todo</button>
</form>
  <div class="todo-list" v-bind:key="todo.id" v-for="todo in todos">
  <span>
  <input type="checkbox" @change="checkUncheck(todo)"/>
      <span v-bind:style="{'text-decoration': (todo.isSelected ? 'line-through' : 'none')}">{{todo.name}}</span>
      <button @click="deleteItem(todo)" v-bind:style="{color: 'red', marginLeft: '20px'}">Delete X</button>
</span>
  </div>
</div>

</template>
<script>
export default {
  name: 'TodoList',
  data() {
    return {
      todoName: ""
    }
  },
  props: {
    todos: Array
  },
  methods: {
  handleSubmit(e) {
    e.preventDefault();
    const todo = {id: (this.todos.length === 0 ? 1 : this.todos[this.todos.length - 1]["id"] + 1),
     name: this.todoName,
      age: 25,
      isSelected: false};
    this.todos = [...this.todos, todo];
    this.todoName = "";
  },
  changeTodoName(value) {
    this.todoName = value
  },
    checkUncheck(todo) {
      const todos = this.todos;
      for (let i in todos) {
        if (todos[i].id === todo["id"]) {
          todos[i].isSelected = !todos[i].isSelected
        }
      }
    },
    deleteItem(todo) {
    const todos = this.todos;
      for (let i in todos) {
        if (todos[i]["id"] === todo.id) {
          todos.splice(i, 1);
        }
      }
    }
  }
}
</script>

<style scoped>
.red {
  color: red
};
.green {
  color: green !important;
  text-decoration: line-through
};
.blue {
  color: blue
}
</style>


//<form v-on:submit="handleSubmit">
//<button v-on:click="deleteItem(todo)" v-bind:style="{color: 'red', marginLeft: '20px'}">Delete X</button>
//<input type="checkbox" v-on:change="checkUncheck(todo)"/>
