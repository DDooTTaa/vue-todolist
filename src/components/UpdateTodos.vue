<template>
  <div>
    <input v-show="toggleFlag" v-model="str" type="text" @keypress.enter="switchUpdate"/>
    <button v-show="!toggleFlag" @click="switchToggle">수정</button>
  </div>
</template>
<script>
export default {
  props: {
    text: {
      type: String,
      default: ''
    },
    index: {
      type: Number,
      default: null
    }
  },
  data() {
    return {
      toggleFlag: false,
      str: ''
    }
  },
  watch: {
    //watch로 props 를 변경한다.
    text: {
      immediate: true,
      handler(str) {
        this.str = str;
      }
    },
  },
  methods: {
    //버튼과 input 박스를 스위치한다.
    switchUpdate() {
      this.$emit('updateList', this.str, this.index);
      this.switchToggle();
    },
    switchToggle() {
      this.toggleFlag = !this.toggleFlag;
    },
  },
};
</script>
<style scoped>
</style>
