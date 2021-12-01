<template>
    <ul>
      <li
        v-for="(text, index) in todos"
        :key="index"
      >
          <label>{{ text }}</label>
        <UpdateTodos :text="text" />
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
      deep: true,
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
  }
}
</script>

<style scoped>
</style>
