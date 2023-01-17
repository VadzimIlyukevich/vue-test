<script>
import axios from "axios";
import PostList from "@/componets/PostList.vue";
import PostForm from "@/componets/PostForm.vue";

export default {
  components:{
    PostList,
    PostForm,
  }
  ,
  data() {
    return {
      posts: [],
      dialogVisible: false,
      isPostsLoading: false,
      selectedSort: '',
      sortOptions: [
        {value: 'title', name: 'по названию'},
        {value:  'body', name: 'по содержанию'},
      ]
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
  },
  computed:{
    sortedPosts(){
      return [...this.posts].sort((post1, post2) => post1[this.selectedSort]?.localeCompare(post2[this.selectedSort]))
    }
  },
}
</script>

<template>
  <div class="app">
    <h1 class="title">Страница с постами</h1>
    <div class="app_btns">
    <post-button @click="showDialog">Создать пост</post-button>
      <PostSelect
          v-model="selectedSort"
          :options="sortOptions"
      ></PostSelect>
    </div>
    <post-dialog v-model:show="dialogVisible">
      <PostForm @create="createPost"/>
    </post-dialog>

    <PostList :posts="sortedPosts" @remove="removePost" v-if="!isPostsLoading"/>
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
.app_btns{
  margin: 10px 0;
  display: flex;
  justify-content: space-between;
}
</style>
