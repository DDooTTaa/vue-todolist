<template>
  <div>
    <input v-show="toggleUpdate" type="text" v-model="text" @keypress.enter="updateTodo"/>
    <button v-show="!toggleUpdate" @click="updateTodo">수정</button>
  </div>
</template>
<script>
export default {
  data() {
    return {
      toggleUpdate: false,
      arr: ""
    }
  },
  props: {
    text: {
      type: String,
      default: ""
    },
  },
  watch: {
    //watch로 props 를 변경한다.
    text: {
      deep: true,
      immediate: true,
      handler(arr) {
        this.arr = arr;
      }
    },
  },
  methods: {
    //버튼과 input 박스를 스위치한다.
    updateTodo() {
      this.toggleUpdate = !this.toggleUpdate;
    },
  },
}
</script>
<style scoped>
</style>
