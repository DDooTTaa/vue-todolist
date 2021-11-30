<template>
  <div>
    <input v-show="toggleUpdate" type="text" v-model:value="text.todo" @keypress.enter="setTodo"/>
    <button v-show="!toggleUpdate"  @click="updateTodo">수정</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      toggleUpdate: false,
    }
  },
  props: {
    todos: {
      type: Array,
      default: []
    },
    text: {
      type: Object
    }
  },
  methods: {
    updateTodo() {
      console.log(this.text);
      this.toggleUpdate = true;

    },
    setTodo() {
      if (this.text.todo !== "") {
        //App 으로 이벤트와 todo 를 보낸다
        this.todos.push(this.text.todo);
        this.toggleUpdate = false;
      }
    }
  }
}
</script>

<style scoped>
.hide{
  display: none;
}

</style>
