<template>
  <button @click="updateTodo">수정</button>

</template>

<script>
export default {
  name: "Delete",
  methods: {
    updateTodo(event) {
      const list = event.target.parentElement;
    }
  },
}
</script>

<style scoped>

</style>
