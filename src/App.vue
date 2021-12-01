<template>
  <div>
      <TodoInput @insert="insertTodo"/>
      <button @click="destroyAll">전체 삭제</button>
      <body-list :todos="todos" />
  </div>
</template>

<script>
import TodoInput from "./components/TodoInputr";
import BodyList from "./components/BodyList";

export default {
  components: {
    TodoInput, BodyList
  },
  data() {
    return {
      todos: []
    };
  },
  mounted() {
    window.addEventListener('beforeunload', (event) => {
      //  preventDefault는 호출해야하며, 기본 동작을 방지합니다.
        event.preventDefault();
        event.returnValue = '';
    }
    );
  },
  methods: {
    insertTodo(todo) {
      this.todos.push(todo);
      // this.todos = [
      //   ...this.todos, // 기존의 배열에 새로운 todo 를 추가.
      //   {
      //     todo // 현재 입력된 text를 todos 에 저장
      //   }
      // ];
    },
    destroyAll() {
      this.todos = [];
    },
  }
};
</script>
<style>
li {
  margin: 10px;
}
</style>
