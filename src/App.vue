<template>
  <div id="app">
    <Addtodo />
    <Filtertodo />
    <Todo />
  </div>
</template>

<script>
import Todo from './components/Todo.vue'
import Addtodo from './components/Addtodo.vue'
import Filtertodo from './components/Filtertodo.vue'

export default {
  name: 'App',
  components: {
    Todo,
    Addtodo,
    Filtertodo
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
