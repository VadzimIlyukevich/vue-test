<script>
import PostForm from "@/componets/PostForm.vue";
import PostList from "@/componets/PostList.vue";
import PostDialog from "@/componets/UI/PostDialog.vue";
import PostButton from "@/componets/UI/PostButton.vue";
import axios from "axios";

export default {
  components:{
    PostButton,
    PostDialog,
    PostList, PostForm
  }
  ,
  data() {
    return {
      posts: [],
      dialogVisible: false,
      isPostsLoading: false,
    }
  },
  methods: {
    createPost(post){
      this.posts.push(post);
      this.dialogVisible = false
    },
    removePost(post){
      this.posts = this.posts.filter(p => p.id !== post.id)
    },
    showDialog(){
      this.dialogVisible = true
    },
    async fetchPosts(){
      try {
        this.isPostsLoading = true
        const response = await axios.get('https://jsonplaceholder.typicode.com/posts?_limit=10')
        this.posts = response.data
      } catch (e){
        alert('Ошибка')
      } finally {
        this.isPostsLoading = false
      }
    }
  },
  mounted() {
    this.fetchPosts()
  }
}
</script>

<template>
  <div class="app">
    <h1 class="title">Страница с постами</h1>
    <div class="flex">
    <post-button @click="showDialog">Создать пост</post-button>
    </div>
    <post-dialog v-model:show="dialogVisible">
      <PostForm @create="createPost"/>
    </post-dialog>

    <PostList :posts="posts" @remove="removePost" v-if="!isPostsLoading"/>
    <div class="download" v-else-if="isPostsLoading">Идёт загрузка</div>
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

.title{
  color: white;
  padding: 10px 15px;
  border: 1px dashed white;
  text-align: center;
}
.download{
  color: white;
}
</style>
