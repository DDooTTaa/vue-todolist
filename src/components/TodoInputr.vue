<template>
  <div>
    <h1>todos</h1>
    <input
      placeholder="할일을 입력해주세요"
      v-model="todo"
      @keypress.enter="setTodo"
    />
  </div>
</template>
<script>
export default {
  data() {
    return {
      todo: ""
    };
  },
  methods: {
    setTodo() {
      if (this.todo !== "") {
        //App 으로 이벤트와 todo 를 보낸다
        this.$emit("insert",this.todo);
        this.todo = "";
      }
    },
  }
};
</script>
