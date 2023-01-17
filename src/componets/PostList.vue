<template>
  <div v-if="posts.length > 0">
    <hr class="separator">
    <h2 class="title">Список постов</h2>
    <transition-group name="post-list">
      <post-item
          v-for="post in posts"
          :post="post"
          :key="post.id"
          @remove="$emit('remove', post)"
      />
    </transition-group>

  </div>
  <div v-else>
    <hr class="separator">
    <h2 class="title">Список постов пуст</h2>
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

.separator{
  color: white;
}

</style>