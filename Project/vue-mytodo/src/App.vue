<template>
  <div id="TodoContainer">
    <TodoHeader />
    <TodoInput v-on:createTodo="addTodo" />
    <TodoList :todos="todos" :changeState="changeState" />
    <TodoFooter />
  </div>
</template>

<script>
import TodoHeader from "./components/TodoHeader";
import TodoInput from "./components/TodoInput";
import TodoList from "./components/TodoList";
import TodoFooter from "./components/TodoFooter";

export default {
  name: "App",
  components: {
    TodoHeader,
    TodoInput,
    TodoList,
    TodoFooter,
  },
  data: function() {
    return {
      todos: [
        {
          id: 1,
          text: "밥 먹기",
          checked: true,
        },
        {
          id: 2,
          text: "공부하기",
          checked: true,
        },
        {
          id: 3,
          text: "잠 자기",
          checked: false,
        },
        {
          id: 4,
          text: "씻기",
          checked: true,
        },
        {
          id: 5,
          text: "물고기 밥 주기",
          checked: false,
        },
      ],
    };
  },
  methods: {
    addTodo: function(msg) {
      this.todos.push({
        id: this.todos.length + 1,
        text: msg,
        checked: false,
      });
    },
    changeState(id) {
      console.log(id);
      this.todos = this.todos.map((item) => {
        if (item.id === id) {
          return (item.checked = !item.checked);
        }
      });
    },
  },
};
</script>

<style>
#app {
  display: flex;
  justify-content: center;
  align-items: center;
}

#TodoContainer {
  width: 50%;
  height: 70%;
}
</style>
