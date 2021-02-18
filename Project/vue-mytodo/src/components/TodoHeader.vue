<template>
  <div id="header">
    <h1>Wanseo's Todo List</h1>
  </div>
</template>

<script>
export default {
  name: "TodoHeader",
};
</script>

<style scoped>
#header {
  display: flex;
  height: 20%;
  justify-content: center;
  align-items: center;
  background-color: #a5b3f5;
}

h1 {
  font-size: 35px;
}
</style>
