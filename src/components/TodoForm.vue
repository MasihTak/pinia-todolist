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

<style scoped>
form {
    display: flex;
    justify-content: center;
    align-items: center;
    margin-bottom: 15px;
}
input {
    margin-top: 25px;
    margin-bottom: 15px;
    height: 20px;
    width: 50%;
}
button {
    margin-left: 30px;
    background-color: #39D106;
    padding: 5px 10px;
    border: none;
    border-radius: 5px;
    font-weight: 800;
    color: white;
}
.alert-div {
    min-height: 25px;
}
.alert {
    color: #D1495B;
    font-size: 1em;
    font-weight: 600;
}

</style>
