<template>
    <ul>
      <li
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
      default: () => []
    }
  },
  watch: {
    todos:{
      //deep = todos 배열 내부가 변경될 수 있도록 한다
      deep: true,
      //immediate = 컴포넌트가 성성될 때 핸들러를 실행한다
      immediate: true,
      handler(arr){
       this.arr = arr;
      }
    }
  },
  methods: {
    deleteTodo(index) {
       //index 위치의 원소 하나 삭제 * 1 없으면 뒤를 다 삭제한다.
      this.arr.splice(index, 1);
    },
    TodoConvert(text, index) {
      console.log("??");
          if(this.arr[index] !== text) {
            this.arr.splice(index, 1, text);
      }
    }
  }
}
</script>

<style scoped>
</style>
