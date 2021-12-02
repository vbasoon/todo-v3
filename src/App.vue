<template>
  <header></header>
  <main>
    <section class="todo">
      <h1 class="todo__heading">{{ heading }}</h1>
      <div class="todo__wrapper">
        <TodoForm :title="title" @addTodo="addTask" />
        <TodoList :todos="todos" :title="title" :filtered="filtered" />
      </div>
    </section>
  </main>
</template>

<script>
import "./assets/scss/style.scss";
import TodoForm from "./components/v-todo-form.vue";
import TodoList from "./components/v-todo-list.vue";
//const STORAGE_KEY = "storage-todo";
export default {
  name: "App",
  data() {
    return {
      heading: "Todo App",
      todos: [],
      title: "",
    };
  },
  components: {
    TodoForm,
    TodoList,
  },
  created() {
    this.todos = JSON.parse(localStorage.getItem("todos") || "[]");
  },
  mounted() {
    fetch("https://jsonplaceholder.typicode.com/todos").then((res) =>
      res.json().then((data) => (this.todos = data))
    );
    console.log(this.todos);
  },
  computed: {
    filtered() {
      //all
      if (this.filter === "all") {
        return this.todos;
      } else if (this.filter === "active") {
        return this.todos.filter(function (todo) {
          return !todo.completed;
        });
      } else {
        return this.todos.filter(function (todo) {
          return todo.completed;
        });
      }
    },
  },
  methods: {
    addTask(title) {
      console.log(this.todos);

      if (!title) {
        alert("Please add a task");
        return;
      }
      const newTask = {
        userId: 1,
        id: this.todos.length + 1,
        title,
        completed: false,
      };

      /* this.todos = JSON.parse(localStorage.getItem("todos") || "[]");*/
      this.todos = [newTask, ...this.todos];
      //let s2 = this.todos.unshift(newTask);

      localStorage.setItem("todos", JSON.stringify(this.todos));
    },
  },
};
</script>
<style lang="scss"></style>
