<script>
import PostForm from "@/componets/PostForm.vue";
import PostList from "@/componets/PostList.vue";
import PostDialog from "@/componets/UI/PostDialog.vue";
import PostButton from "@/componets/UI/PostButton.vue";

export default {
  components:{
    PostButton,
    PostDialog,
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
      dialogVisible: false,
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
    }
  }
}
</script>

<template>
  <div class="app">
    <h1 class="title">Страница с постами</h1>
    <post-button @click="showDialog">Создать пользователя</post-button>
    <post-dialog v-model:show="dialogVisible">
      <PostForm @create="createPost"/>
    </post-dialog>

    <PostList :posts="posts" @remove="removePost"/>
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
</style>
