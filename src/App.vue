<template>
  <div id="app">

    <TodoInput />
    <TodoList :todolist="todoList" />
  </div>
</template>

<script>
import axios from 'axios'
import TodoInput from './components/TodoInput.vue';
import TodoList from './components/TodoList.vue';

export default {
  name: 'App',
  components: {
    TodoInput,
    TodoList,
  },
  data() {
    return {
      todoList: [],
    }
  },
  watch: {
    todoList: function(newVal) {
      console.log(newVal)
    }
  },
  methods: {
    async getData() {

      const { data } = await axios.get("http://localhost:8080/board/list")

      if(data) {
        this.todoList = data
      }
    
    }
  },

  mounted() {
    this.getData();
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
