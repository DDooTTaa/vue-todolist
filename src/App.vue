<template>
  <div>
      <TodoInput @insert="insertTodo"/>
    <div class="destroy">
      <button class="destroyBtn" @click="destroyAll">All List Delete</button>
    </div>
      <body-list :todos="todos" />
    <div class="example">
      <my-component></my-component>
    </div>
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
    this.blockUnload();
  },
  methods: {
    blockUnload() {
      window.addEventListener('beforeunload', (event) => {
          //  preventDefault는 호출해야하며, 기본 동작을 방지합니다.
          event.preventDefault();
          event.returnValue = '';
        }
      );
    },
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
.destroy {
  position: fixed;
  top: 20%;
  left: 95%;
}

.destroyBtn{
  background-color: white;
  color: black;
  border: 2px solid gray;
  border-radius: 10% 0% 0% 0%;
}
.destroyBtn {

}
</style>
