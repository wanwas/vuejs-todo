<template>
  <div class="container">
    <HeaderContent />
    <TodoList @remove-todo="removeTodo" @change-status="changeStatus" @create-todo="createTodo" v-bind:todos="todos" /> 
  </div>
</template>

<script>
import HeaderContent from "@/components/HeaderContent";
import TodoList from "@/components/TodoList"

export default {
  name: "App",
  components: {HeaderContent, TodoList},
  data() {
    return {
      todos: [],
    };
  },
  methods: {
    removeTodo(id) {
      this.todos = this.todos.filter(todo => todo.id != id)
    },
    createTodo(newTodo) {
      this.todos.unshift(newTodo)
    },
    changeStatus(index) {
      this.todos[index].completed = !this.todos[index].completed;
    }

  },
  mounted() {
    fetch("https://jsonplaceholder.typicode.com/todos?_limit=25")
      .then((response) => response.json())
      .then((json) => {
        this.todos = json;
      });
  },
}
</script>

<style>
* {
  box-sizing: border-box;
}
body {
  margin: 0;
  padding: 0;
}
#app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>
