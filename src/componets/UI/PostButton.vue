<template>
  <button class="button">
    <slot></slot>
  </button>
</template>

<script>
export default {
  name: "PostButton"
}
</script>

<style scoped>

.button{
  padding: 10px 15px;
  font-size: 14px;
  color: teal;
  background: none;
  border: 1px solid teal;
}

.button:active{
  background: teal;
  color: white;
  border: 1px solid white;
}

</style>