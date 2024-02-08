<script setup>
import { ref } from "vue";
import { useStore } from "vuex";

const store = useStore();
const inputModel = ref("");

function onAdd(e) {
  console.log("add");
  store.commit("todos/create", inputModel.value);
  inputModel.value = "";
  e.target.blur();
}
</script>

<template>
  <div class="todo-input">
    <q-input
      outlined
      clearable
      v-model="inputModel"
      name="todo"
      @keyup.enter="onAdd"
      placeholder="New todo"
      bg-color="grey-1"
    />
  </div>
</template>

<style lang="scss" scoped>
.todo-input {
  background: var(--todo-bg-color);
  padding: 1rem;
  border-radius: 0.3rem;
}
</style>
