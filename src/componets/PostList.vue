<template>
  <div>
    <h3 class="title">Список постов</h3>
      <post-item
          v-for="post in posts"
          :post="post"
      />
  </div>
</template>

<script>
import PostItem from "@/componets/PostItem.vue";

export default {
  name: "PostList",
  components: {PostItem},
  props: {
    posts: {
      type:Array,
      required:true,
    }
  }
}
</script>

<style scoped>

.title{
  color: white;
  padding: 10px 15px;
  border: 1px dashed white;
  text-align: center;
}

</style>