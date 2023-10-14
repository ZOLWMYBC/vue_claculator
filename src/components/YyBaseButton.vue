<template>
  <button class="base-button">
    <slot></slot>
  </button>
</template>

<script>
export default {

}
</script>

<style scoped>
.base-button {
  cursor: pointer;
  flex: 1 1 20%;
  width: 45px;
  height: 80px;
  line-height: 80px;
  border-radius: 15px;
  background-color: #f2d7e8;
  font-family: Arial, Helvetica, sans-serif;
  font-weight: bold;
  font-size: 2rem;
  text-align: center;
  box-shadow: 0 0 3px rgba(0, 0, 0, 0.4);
}
</style>