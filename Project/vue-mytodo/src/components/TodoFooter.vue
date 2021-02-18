<template>
  <div id="footer">
    <h4 id="footerText">
      Always do your best
    </h4>
  </div>
</template>

<script>
export default {
  name: "TodoFooter",
};
</script>

<style scoped>
#footer {
  width: 100%;
  height: 13%;
  background-color: #f5c172;
  display: flex;
  justify-content: center;
  align-items: center;
}

#footerText {
  font-size: 23px;
  font-weight: bold;
}
</style>
