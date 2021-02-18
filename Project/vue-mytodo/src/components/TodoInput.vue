<template>
  <form id="todoAddForm" @submit.prevent="createTodo(msg)">
    <input
      id="formInputBox"
      type="text"
      v-model="msg"
      placeholder="write your tasks"
      autocomplete="off"
      ref="todoInput"
    />
    <button id="formSubmitBtn" type="submit">추가</button>
  </form>
</template>

<script>
export default {
  name: "TodoInput",
  props: ["addTodo"],
  methods: {
    createTodo(msg) {
      this.$emit("createTodo", msg);
      this.$refs.todoInput.value = "";
    },
  },
};
</script>

<style scoped>
#todoAddForm {
  width: calc(100% - 2px);
  height: 7%;
  display: flex;
  border: 1px solid #443926;
}

#formInputBox {
  width: 80%;
  height: 97%;
  border: none;
  color: black;
  font-size: 20px;
  background-color: #a5b3c5;
  outline: none;
}

#formSubmitBtn {
  width: 20%;
  height: 100%;
  border: none;
  border-left: 1px solid #443926;
  background-color: #99e299;
  outline: none;
}
</style>
