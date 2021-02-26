<template>
  <input type="text" v-model="inputMessage" />
  <button type="button" @click="createTodo(inputMessage)">추가</button>
  <ul>
    <li v-for="item in todos" v-bind:key="item.id" @click="changeDone(item.id)">
      {{ item.msg }}
      <span v-if="item.done">V</span>
      <span v-else>X</span>
      <button type="button" @click="deleteTodo(item.id)">삭제</button>
    </li>
  </ul>
</template>

<script>
export default {
  name: "TodoList",
  data() {
    return {
      inputMessage: "",
      todos: [
        {
          id: 1,
          msg: "가",
          done: false,
        },
        {
          id: 2,
          msg: "나",
          done: true,
        },
      ],
    };
  },
  methods: {
    createTodo(message) {
      if (message == "") return;
      this.todos.push({
        id: this.todos.length + 1,
        msg: message,
      });
      this.inputMessage = "";
    },
    changeDone(itemID) {
      this.todos.map((item) => {
        if (itemID == item.id) item.done = !item.done;
      });
    },
    deleteTodo(itemID) {
      this.todos.splice(itemID - 1, 1);
    },
  },
};
</script>

<style scoped>
input {
  margin-top: 50px;
}

li {
  margin: 10px 0 10px 0;
  clear: both;
  float: left;
}

span {
  margin-right: 30px;
}
</style>
