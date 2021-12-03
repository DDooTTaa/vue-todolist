<template>
  <div class="header">
    <h1>todos</h1>
    <input type="text" placeholder="Your Todo" v-model="todo" @keypress.enter="setTodo"
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
    //App 으로 이벤트와 입력된 text 를 보낸다
    setTodo() {
      if (this.todo !== "") {
        this.$emit("insert", this.todo);
        this.todo = "";
      }
    },
  }
};
</script>
<style scoped>
.header {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}
h1 {
  font-size: 3.2rem;
}
input {
  width: 20%;
  margin-top: 3%;
  border: none;
  border-bottom: black 1px solid;
  font-size: 0.9rem;
  text-align: center;
}
input:focus {
  outline: none;
}
</style>
