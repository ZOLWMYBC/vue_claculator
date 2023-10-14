<template>
  <div class="footer">
    <slot></slot>

  </div>
</template>

<script>

export default {
}
</script>

<style scoped>
.footer {
  display: flex;
  flex-wrap: wrap;
  padding: 10px;
  gap: 2px;
  width: 316px;
  height: 400px;
  background-color: #f4e9f0;
  text-align: center;
  border: 2px solid #888;
  border-radius: 10px;
  box-shadow: 0 0 5px rgb(0, 0, 0, 0.3);
}
</style>