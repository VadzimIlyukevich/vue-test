<template>
  <input :value="modelValue" @input="updateInput" class="input" type="text">
</template>

<script>
export default {
  name: "PostInput",
  props: {
    modelValue: [String, Number]
  },
  methods:{
    updateInput(event) {
      this.$emit("update:modelValue", event.target.value)
    }
  }
}
</script>

<style scoped>
.input {
  width: 90%;
  border: 1px solid teal;
  padding: 10px 15px;
  margin: 10px 10px;
}
</style>