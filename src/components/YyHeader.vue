<template>
  <div class="header">
    <slot></slot>
  </div>
</template>

<script>
export default {

}
</script>

<style scoped>
.header {
  width: 298px;
  height: 100px;
  line-height: 100px;
  padding: 0 20px;
  background-color: #f4e9f0;
  text-align: right;
  font-size: 2rem;
  font-family: Arial, Helvetica, sans-serif;
  font-weight: bold;
  border-radius: 10px;
  border: 2px solid #888;
  box-shadow: 0 0 5px rgb(0, 0, 0, 0.3);
}
</style>