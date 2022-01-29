<template>
  <div class="todo">
    <h2>Detail todo</h2>
    <h4>{{ todo?.title }}</h4>
    <div v-if="load">Loading ...</div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      todo: null,
      load: true,
    };
  },
  created() {
    this.getTodo();
  },
  methods: {
    getTodo() {
      axios
        .get(
          `https://jsonplaceholder.typicode.com/todos/${this.$route.params.id}`
        )
        .then((res) => (this.todo = res.data))
        .catch((err) => alert(err))
        .finally(() => (this.load = false));
    },
  },
};
</script>
