<script>
import PostForm from "@/componets/PostForm.vue";
import PostList from "@/componets/PostList.vue";

export default {
  components:{
    PostList, PostForm
  }
  ,
  data() {
    return {
      posts: [
        {id: 1, title: 'JavaScript', body: 'ТОП'},
        {id: 2, title: 'Python', body: 'ТОП'},
        {id: 3, title: 'C++', body: 'ТОП'},
      ],
    }
  },
  methods: {
    createPost(post){
      this.posts.push(post);
    }
  }
}
</script>

<template>
  <div class="app">
    <PostForm @create="createPost"/>
    <PostList :posts="posts" />
  </div>
</template>

<style scoped>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.app {
  padding: 20px;
}

</style>
