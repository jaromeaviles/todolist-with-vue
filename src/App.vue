<template>
  <h1>Todos</h1>
  <div class="container">
    <div class="row">
      <div class="col-12">
        <ul>
          <li class="row align-items-center justify-content-center" v-for="todo in todos" :key="todo.id">
            <div class="col-10 text-left">
              {{ todo.todoName }}
            </div>
            <div class="col-2 close-container">
             <i class="fa-solid fa-circle-xmark text-danger" @click="deleteTodo(todo.id)"></i>
            </div>
          </li>
        </ul>
        <add-todo @added-todo="addTodo"></add-todo>
      </div>
    </div>
  </div>
</template>

<script>
import AddTodo from "./components/AddTodo.vue";
export default {
  name: "App",
  data() {
    return {
      todos: [],
    };
  },
  components: {
    AddTodo,
  },
  methods: {
    addTodo(todo) {
      this.todos.unshift(todo);
    },
    deleteTodo(id) {
      let index = this.todos.findIndex(res => {
        return res.id === id;
      });
      this.todos.splice(index, 1);
    }
  },

};
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

.container {
  max-width: 500px;
}

h1 {
  font-size: 60px;
  margin-bottom: 35px;
  font-weight: bold;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  padding: 5px 0;
  font-size: 25px;
  text-align: left;
  margin: 10px 0;
}
.fa-solid {
  font-size: 40px;
  cursor: pointer;
}

.close-container {
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
