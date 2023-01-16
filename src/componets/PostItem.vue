<template>
  <div class="post">
    <div>
      <div>Название: {{ post.title }}</div>
      <div>Описание: {{ post.body }}</div>
    </div>
    <div class="post__btns">
      <button class="button">Удалить</button>
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

.button{
  align-self: flex-end;
  margin-bottom: 10px;
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