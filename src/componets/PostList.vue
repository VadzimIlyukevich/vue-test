<template>
  <div class="post" v-for="post in posts">
    <div>Название: {{ post.title }}</div>
    <div>Описание: {{ post.body }}</div>
  </div>
</template>

<script>
export default {
  name: "PostList",
  props: {
    posts: {
      type:Array,
      required:true,
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
}

</style>