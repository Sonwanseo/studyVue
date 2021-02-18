<template>
  <div id="list">
    <TodoItem
      v-for="item in todos"
      v-bind:key="item.id"
      :id="item.id"
      :text="item.text"
      :checked="item.checked"
      :changeState="changeState"
    />
  </div>
</template>

<script>
import TodoItem from "./TodoItem";

export default {
  name: "TodoList",
  components: {
    TodoItem,
  },
  props: ["todos", "changeState"],
};
</script>

<style scoped>
#list {
  width: 100%;
  height: 60%;
  background-color: gray;
  overflow-y: scroll;
}
</style>
