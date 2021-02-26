<template>
  <TodoList />
</template>

<script>
import TodoList from "@/components/TodoList";

export default {
  name: "App",
  components: {
    TodoList,
  },
};
</script>

<style>
body {
  margin: 0;
  padding: 0;
  width: 100%;
  height: 100vh;
}
</style>
