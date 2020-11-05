<template>
 <div id="app">
    <AddTodo/>
  </div>
</template>

<script>
import AddTodo from './components/AddTodo.vue'

export default {
  name: 'App',
  components: {
    AddTodo
  }
}
</script>

<style>
#app {
 margin:0;
}
</style>
