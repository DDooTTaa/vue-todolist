<template>
  <header class="header">
    <h1>todos</h1>
    <input
      placeholder="할일을 입력해주세요"
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
        // const { todo } = this;
      const todo = this.todo;

        // keyCode 값을 13으로 넣어 엔터로 이벤트를 헨들링한다.
      if (keyCode === 13 &&todo !== "") {
        this.$emit("insertTodo", todo);
        this.todo = "";
      }
    },
  }
};
</script>