<template>
  <div class="post">
    <div>
      <div>Название: {{ post.title }}</div>
      <div>Описание: {{ post.body }}</div>
    </div>
    <div class="post__btns">
      <PostButton>Удалить</PostButton>
    </div>
  </div>
</template>

<script>

export default {
  name: "PostItem",
  props:{
    post:{
      type: Object,
      required: true,
    }
  }
}
</script>

<style scoped>

.post {
  margin-bottom: 5px;
  padding: 15px;
  border: 2px solid teal;
  color: white;
  display: flex;
  align-items: center;
  justify-content: space-between;
}

</style>