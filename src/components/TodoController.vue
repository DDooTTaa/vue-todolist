<template>
  <div>
    <input
      type="text" v-model="saveText" @keyup.enter="updateList" @keyup.esc="outInputBox" v-show="toggleFlag"
    />
    <button v-show="!toggleFlag" @click="updateButton">수정</button>
  </div>
</template>

<script>
export default {
  props: {
    text: String | Number,
    index: Number,
  },
  data() {
    return {
      toggleFlag: false,
      emptyText: '',
      saveText: '',
    };
  },
  watch: {
    text: {
      immediate: true,
      handler(text) {
        this.saveText = text;
      }
    }
  },
  methods: {
    //버튼과 input 박스를 스위치한다.
    switchToggle() {
      if (this.toggleFlag) {
        this.toggleFlag = false;
      } else {
        this.toggleFlag = true;
      }
    },
    //버튼이 눌렸을 때 input 박스가 나오도록 하고 빈 스트링에 현재 스트링 저장
    updateButton() {
      this.switchToggle();
      this.emptyText = this.saveText;
    },
    //엔터를 누르면 BodyList 로 saveText 와 index 를 보낸다
    updateList() {
      this.$emit('update', this.saveText, this.index);
      this.switchToggle();
    },
    //ESC 버튼을 눌렀을 때 이전 입력값을 가져온다.
    outInputBox() {
      this.switchToggle();
      this.saveText = this.emptyText;
    },
  },
};
</script>

<style scoped>
</style>
