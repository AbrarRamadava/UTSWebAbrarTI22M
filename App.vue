<script>
import ToDoList from './components/ToDoList.vue';

export default {
  name: 'App',
  components: {
    ToDoList,
  },
};
</script>

<template>
  <div id="app">
    <h1>ToDoList</h1>
    <ToDoList />
  </div>
</template>

<style scoped>
#app {
  text-align: center;
  font-family: 'Arial', sans-serif;
  padding: 20px;
}

h1 {
  font-size: 2em;
  color: #333;
  margin-bottom: 20px;
  font-weight: 600;
}
</style>
