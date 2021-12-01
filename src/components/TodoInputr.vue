<template>
  <div class="header">
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

<style scoped>
  .header {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
  }
  h1 {
    font-size: 50px;
  }
  input {
    width: 20%;
    margin-top: 3%;
    border: none;
    border-bottom: black 1px solid;
    font-size: 1.2rem;
    text-align: center;
  }
  input:focus{
    outline: none;
  }
  input::placeholder {

  }
</style>
