<template>
  <ul class="todo-section">
    <li class="todo-list" v-for="(text, index) in todos" :key="index">
      <label>{{ text }}</label>
      <update-todos :text="text" :index="index" @update="updateEmit"/>
      <button @click="deleteEmit">X</button>
    </li>
    <button class="destroyButton" @click="destroyEmit">All List Delete</button>
  </ul>
</template>
<script>
import UpdateTodos from './TodoController';
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
    updateEmit(str, index) {
      this.$emit('update', str, index);
    },
    destroyEmit() {
      this.$emit('destroy');
    },
  },
};
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
.destroyButton {
  position: fixed;
  top: 20%;
  left: 95%;
  background-color: white;
  color: black;
  border: 2px solid gray;
}
</style>
