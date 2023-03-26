<script setup>
import { useTodoListStore } from "@/stores/todoList";
import { storeToRefs } from "pinia";

const store = useTodoListStore();

// storeToRefs lets todoList keep reactivity:
const { todoList } = storeToRefs(store);

// destructuring action method doesn't require using storeToRefs:
const { toggleCompleted, deleteTodo } = store;
</script>

<template>
  <div v-for="todo in todoList" :key="todo.id" class="list">
    <div class="item">
      <span :class="{ completed: todo.completed }">{{ todo.item }}</span>
      <span @click.stop="toggleCompleted(todo.id)">&#10004;</span>
      <span @click="deleteTodo(todo.id)">&#10060;</span>
    </div>
  </div>
</template>

<style scoped>
.item span:first-of-type {
  margin-right: 5px;
}

.completed {
  text-decoration: line-through;
}
</style>
