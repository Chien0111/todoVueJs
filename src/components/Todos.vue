<template>
  <AddTodo @add-todo="addTodo" />
  <TodoItem
    v-for="todo in todos"
    :key="todo.id"
    :todoProps="todo"
    @item-completed="markComplete"
    @delete-item="deleteTodo"
  />
</template>

<script>
import { ref } from "vue";
import { v4 as uuidv4 } from "uuid";

import TodoItem from "./TodoItem.vue";
import AddTodo from "./AddTodo.vue";

export default {
  name: "TodoWord",
  components: { TodoItem, AddTodo },
  setup() {
    const todos = ref([
      {
        id: uuidv4(),
        title: "Viec 1",
        completed: false,
      },
      {
        id: uuidv4(),
        title: "Viec 2",
        completed: false,
      },
      {
        id: uuidv4(),
        title: "Viec 3",
        completed: false,
      },
    ]);

    const markComplete = (id) => {
      todos.value = todos.value.map((item) => {
        if (item.id === id) item.completed = !item.completed;
        return item;
      });
    };

    const deleteTodo = (id) => {
      todos.value = todos.value.filter((item) => item.id !== id);
    };

    const addTodo = (newTodo) => {
      todos.value.push(newTodo);
    };

    return {
      todos,
      markComplete,
      deleteTodo,
      addTodo,
    };
  },
  props: {
    msg: String,
  },
};
</script>

<style scoped></style>
