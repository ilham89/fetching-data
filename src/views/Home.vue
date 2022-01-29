<template>
  <div class="container">
    <header>
      <h4>Belajar fetch data</h4>
    </header>
    <div class="list">
      <div v-if="load">Loading ...</div>
      <ul v-for="todo in todos" :key="todo.id" style="list-style: none">
        <li>
          <router-link :to="{ name: 'Todo', params: { id: todo.id } }">{{
            todo.title
          }}</router-link>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import axios from "axios";

export default {
  name: "Home",
  components: {},
  data() {
    return {
      todos: [],
      load: true,
    };
  },
  created() {
    this.getTodos();
  },
  methods: {
    getTodos() {
      axios
        .get(`https://jsonplaceholder.typicode.com/todos`)
        .then((res) => {
          this.todos = res.data;
        })
        .catch((err) => {
          alert(err);
        })
        .finally(() => (this.load = false));
    },
  },
};
</script>
