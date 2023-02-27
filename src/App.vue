<template>
  <HeaderWord />
  <TodoWord />
</template>

<script>
import HeaderWord from "./components/Header.vue";
import TodoWord from "./components/Todos.vue";

export default {
  name: "App",
  components: {
    HeaderWord,
    TodoWord,
  },
  data() {
    return {
      name: "Nguyen Xuan Chien",
      isButtonDisabled: true,
    };
  },
  methods: {
    changeValue(event) {
      this.name = event.target.value;
    },
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
}
</style>
