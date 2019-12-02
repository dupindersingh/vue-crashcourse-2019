<template>
  <div id="app">
    <img v-bind:style="{width: '100px', height: '100px', border: '2px solid seagreen', borderRadius: '100px', padding: '10px'}" alt="Vue logo" src="./assets/logo.png">
    <h1>Welcome to Your Vue.js App</h1>
    <VueInfo title="I love vue"/>
    <HelloWorld v-bind:todos="todos" v-bind:vInfo="vInfo" @againClickCalled="punchMe"/>
  </div>
</template>

<script>
import VueInfo from './components/VueInfo.vue'
import HelloWorld from './components/HelloWorld.vue'
export default {
  name: 'app',
  components: {
    HelloWorld,
    VueInfo
  },
  methods: {
    punchMe(inputValue) {     
      alert(inputValue)
    }
  },
  data() {
  return {
  todos: [{name: "Dupinder", id: 1, age: 24, isSelected: false}, {name: "Amanpreet", id: 2, isSelected: false, age: 26}, {name: "Sandeep Kaur", id: 3, isSelected: false, age: 27}],
  vInfo: "TODO LIST"
  }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
};
</style>
