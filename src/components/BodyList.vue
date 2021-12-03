<template>
  <ul class="todo-section">
    <li class="todo-list" v-for="(text, index) in todos" :key="index">
      <label>{{ text }}</label>
      <update-todos v-bind:text="text" v-bind:index="index" @updateList="updateEmit"/>
      <button @click="deleteEmit">X</button>
    </li>
    <button class="destroyBtn" @click="destroyEmit">All List Delete</button>
  </ul>
</template>
<script>
import UpdateTodos from "./UpdateTodos";

export default {
  components: {
    UpdateTodos
  },
  props: {
    todos: Array,
  },
  methods: {
    deleteEmit(index) {
      this.$emit('delete', index);
    },
    updateEmit(text, index) {
      this.$emit('update', text, index);
    },
    destroyEmit() {
      this.$emit('destroy');
    }
  }
}
</script>
<style scoped>
.todo-list {
  display: flex;
}
.todo-section {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
.destroyBtn {
  position: fixed;
  top: 20%;
  left: 95%;
  background-color: white;
  color: black;
  border: 2px solid gray;
  border-radius: 10% 0% 0% 0%;
}
</style>
