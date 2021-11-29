<template>
  <div id="app">
    <section class="todoapp">
      <Header @insert="insertTodo"/>
      <button @click="destroyAll">전체 삭제</button>
      <body-list :todos="todos" />
    </section>
  </div>
</template>

<script>
import uniqueId from 'lodash.uniqueid'
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
  mounted() {
    window.addEventListener('beforeunload', (event) => {
      // 명세에 따라 preventDefault는 호출해야하며, 기본 동작을 방지합니다.
        event.preventDefault();
        event.returnValue = '';
    }
    );
  },
  methods: {
    insertTodo(text) {
      this.todos = [
        ...this.todos, // 기존의 배열에 새로운 todo 를 추가.
        {
          id: uniqueId(),
          text // 현재 입력된 text 값을 todos 에 저장
        }
      ];
      console.log(this.todos);
    },
    destroyAll() {
      this.todos = [];
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
