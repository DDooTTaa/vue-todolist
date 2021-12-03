<template>
  <div id="app">
    <todo-input @insert="insertTodo"/>
    <body-list v-bind:todos="todos" @destroy="destroyAll" @update="todoUpdate" @delete="deleteTodo"/>
  </div>
</template>
<script>
import TodoInput from "./components/TodoInput";
import BodyList from "./components/BodyList";

export default {
  components: {
    TodoInput,
    BodyList
  },
  data() {
    return {
      todos: [],
    };
  },
  mounted() {
    this.blockUnload();
  },
  methods: {
    // 뒤로가기나 새로고침시 기본 동작을 방지
    blockUnload() {
      window.addEventListener('beforeunload', (event) => {
          event.preventDefault();
        }
      );
    },
    // todos 에 push 함
    insertTodo(todo) {
      this.todos.push(todo);
      console.log(this.todos);
    },
    // 전체에 빈 배열을 할당
    destroyAll() {
      this.todos = [];
    },
    // todos 를 업데이트함
    todoUpdate(text, index) {
      //index 위치의 text 추가하고 원소 하나 삭제.
      this.todos.splice(index, 1, text);
    },
    // todos 배열의 원소를 지움
    deleteTodo(index) {
      this.todos.splice(index, 1);
    }
  }
};
</script>
<style>
li {
  margin: 10px;
  list-style: none;
  padding-bottom: 1rem;
}
label {
  margin: 0px 2rem 0px 0px;
}
</style>
