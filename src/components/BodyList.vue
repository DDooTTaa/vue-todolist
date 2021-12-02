<template>
    <ul class="Body">
      <li
        class="todoList"
        v-for="(text, index) in todos"
        :key="index"
      >
          <label>{{ arr[index] }}</label>
        <UpdateTodos :text="text" :index="index" @updateList="TodoConvert"/>
          <button @click="deleteTodo(index)">X</button>
      </li>
    </ul>
</template>

<script>
import UpdateTodos from "./UpdateTodos";

export default {
  components: {UpdateTodos},
  // props 로 가져온 걸 수정하면 안됨 -> watch
  data() {
    return {
      arr: [],
    }
  },
  props: {
    todos: {
      type: Array,
      default: []
    }
  },
  watch: {
    todos:{
      //deep = todos 배열 내부가 변경될 수 있도록 한다
      // deep: true,
      handler(arr){
       this.arr = arr;
      }
    }
  },
  methods: {
    deleteTodo(index) {
       //index 위치의 원소 하나 삭제.
      this.arr.splice(index, 1);
    },
    TodoConvert(text, index) {
          if(this.arr[index] !== text) {
            //index 위치의 text 추가하고 원소 하나 삭제.
            this.arr.splice(index, 1, text);
      }
    }
  }
}
</script>

<style scoped>
  li {
    list-style:none;
    padding-bottom: 1rem;
  }
  .todoList{
    display: flex;
  }
  .Body{
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }
  label {
    margin: 0px 2rem 0px 0px;
  }
</style>
