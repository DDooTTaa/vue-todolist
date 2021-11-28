<template>
  <header class="header">
    <h1>todos</h1>
    <input
      placeholder="할일읍 입력해주세요"
      v-model="todo"
      @keypress="setTodo"
    />
  </header>
</template>
<script>
export default {
  data() {
    return {
      todo: ""
    };
  },
  methods: {
    setTodo({ keyCode }) {
      const todo = this.todo;
// const { todo } = this;
      if (todo !== "") {
        this.$emit("insertTodo", todo);
        this.todo = "";
      }
    },
  }
};
</script>