<script setup>
import { ref } from "vue";
import { useTodoListStore } from "@/stores/todolist";

const todo = ref("");

// local store
const store = useTodoListStore();

function addItemAndClear(item) {
  if (item.length === 0) {
    return;
  }

  store.addTodo(item);
  todo.value = "";
}
</script>

<template>
  <form @submit.prevent="addItemAndClear(todo)">
    <input v-model="todo" /> <button>Add</button>
  </form>
</template>

<style scoped></style>
