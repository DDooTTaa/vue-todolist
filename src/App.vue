<template>
  <div id="app">
    <section class="todoapp">
      <Header @insertTodo="insertTodo" />
      <button v-on:click="destroyAll">전체 삭제</button>
      <body-list :todos="todos" />
    </section>
  </div>
</template>

<script>
import Header from "./components/Header";
import BodyList from "./components/BodyList";
export default {
  components: {
    Header, BodyList
  },
  data() {
    return {
      todos: []
    };
  },
  methods: {
    insertTodo(text) {
      this.todos = [
        ...this.todos, // 기존의 배열에 새로운 todo 를 추가합니다.
         {
          // id의 경우 같은 포맷을 유지하기 때문에 새로 받지 않습니다. 
          id: new Date().getTime(), 
          text, // 유동적인 text 값만 받습니다.
        }
      ];
    },
    destroyAll() {
      console.log("dadada");
        this.todos.splice(0);
    }

  }
};
</script>


<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
