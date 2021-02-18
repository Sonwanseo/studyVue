<template>
  <div class="item">
    <div class="textBox">{{ text }}</div>
    <div class="stateBtn" v-if="checked == true" @click="changeState(id)">
      ✔
    </div>
    <div class="stateBtn" v-else @click="changeState(id)">X</div>
    <button class="deleteBtn">-</button>
  </div>
</template>

<script>
export default {
  name: "TodoItem",
  props: ["id", "text", "checked", "changeState"],
};
</script>

<style scoped>
.item {
  width: 100%;
  height: calc(20% - 1px);
  background-color: #72b5f5;
  border-bottom: 1px solid black;
  display: flex;
  justify-content: space-around;
  align-items: center;
}

.textBox {
  width: 70%;
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  font-size: 20px;
}

.stateBtn {
  width: 5%;
  height: 40%;
  display: flex;
  justify-content: center;
  align-items: center;
  cursor: pointer;
}

.deleteBtn {
  width: 5%;
  height: 40%;
  border: none;
  opacity: 0.7;
  outline: none;
  cursor: pointer;
}
</style>
