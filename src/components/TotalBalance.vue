<template>
  <div class="container">
    <div class="balance">
      <h3>Balance : {{ total }}</h3>
    </div>
  </div>
</template>

<script>
export default {
  name: "TotalBalance",
  props: {
    total: {
      type: Number,
      default: 0,
    },
  },
};
</script>

<style scoped>
.balance {
  width: 400px;
  text-align: center;
  margin: 5px;
  padding: 15px 10px;
  font-family: Helvetica;
  background-color: rgb(242, 242, 242);
  border-radius: 10px;
  max-width: 400px;
}
</style>
