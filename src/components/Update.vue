<template>
  <button @click="updateTodo">수정</button>

</template>

<script>
export default {
  name: "Delete",
  props: {
    todos: { type: Array, default: () => [] }
  },
  methods: {
    updateTodo() {
      const { todos } = this;
      console.log(todos);
    }
  }
}
</script>

<style scoped>

</style>
