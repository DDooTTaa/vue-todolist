<template>

  <button @click="deleteTodo">X</button>
</template>

<script>
export default {
  props: {
    todos: { type: Array, default: () => [] }
  },
  name: "Delete",
  methods: {
    deleteTodo(event) {
      event.target.parentElement.remove();
    }
  },
}
</script>

<style scoped>

</style>
