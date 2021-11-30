<template>
    <ul>
      <li
        v-for="(text, index) in todos"
        :key="index"
      >
<!--          <p> {{ index }}</p>-->
          <label>{{ text.todo }}</label>
        <UpdateTodos :text="text"/>
          <button @click="deleteTodo(index)">X</button>
      </li>
    </ul>
</template>

<script>
import UpdateTodos from "./UpdateTodos";

export default {
  components: {UpdateTodos},
  // props 로 가져오면 데이터 수정이 불가능 -> watch 가 필요하다
  // 하지만 watch를 사용하지 않고도 삭제가 가능하다 왜? -> BodyList에서 v-for 을 통해 index를 정의해주기 때문인가?
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
      // console.log(index);
      // console.log(this.arr[index]);
       //const { todos } = this;
       //index 위치의 원소 하나 삭제 * 1 없으면 뒤를 다 삭제한다.
      this.arr.splice(index, 1);
    },
  }
}

</script>

<style scoped>

</style>
