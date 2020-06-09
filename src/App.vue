<template>
  <div id="app">
    <Home msg="Todo App" />
    <i @click="toogleAddTodo" class="fas fa-plus"></i>
    <div v-if="addTodo" class="addTodo">
      <AddTodo v-on:addTodoEvent="addTodoMethod($event)" />
    </div>
    <div v-bind:key="todo.id" v-for="todo in todos">
      <Todo
        :data="todo"
        v-on:makeImportantEvent="makeImportant($event)"
        v-on:deleteTodoEvent="deleteTodo($event)"
        v-on:todoDoneEvent="todoCompleted($event)"
      />
    </div>
  </div>
</template>

<script>
import Home from "./components/Home.vue";
import AddTodo from "./components/AddTodo.vue";
import Todo from "./components/Todo.vue";

export default {
  name: "App",
  data() {
    return {
      addTodo: false,
      todos: [
        {
          id: 6,
          name: "Playing Cricket",
          completed: true,
          important: false,
        },
        {
          id: 5,
          name: "Making a React application",
          completed: true,
          important: false,
        },
        {
          id: 4,
          name: "Reading for the exams",
          completed: false,
          important: true,
        },
        {
          id: 3,
          name: "Android app project",
          completed: true,
          important: false,
        },
        {
          id: 2,
          name: "Attend RCF DevTeam meeting",
          completed: false,
          important: true,
        },
        {
          id: 1,
          name: "Making a Vue application",
          completed: true,
          important: false,
        },
      ],
    };
  },
  components: {
    Home,
    AddTodo,
    Todo,
  },
  methods: {
    toogleAddTodo() {
      this.addTodo = !this.addTodo;
    },
    deleteTodo(id) {
      this.todos = this.todos.filter((todo) => todo.id !== id);
    },
    addTodoMethod(input) {
      this.todos.unshift({
        id: this.todos.length + 1,
        name: input,
        completed: false,
        important: false,
      });
    },
    makeImportant(id) {
      this.todos.map((todo) => {
        if (todo.id === id) {
          todo.important = !todo.important;
        }
      });
    },
    todoCompleted(id) {
      this.todos.map((todo) => {
        if (todo.id === id) {
          todo.completed = !todo.completed;
        }
      });
    },
  },
};
</script>

<style>
body {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
  background: #42b983;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #101e2c;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
.fa-plus {
  color: #fff;
  border: 2px solid #42b983;
  cursor: pointer;
  margin-bottom: 10px;
}
</style>
