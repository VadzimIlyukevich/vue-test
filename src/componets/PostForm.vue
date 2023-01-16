<template>
  <form @submit.prevent>
    <h4 class="title">Создание поста</h4>
    <input class="input"
           type="text"
           placeholder="Название"
           v-model="post.title"
    >

    <input class="input"
           type="text"
           v-model="post.body"
    >

    <button
        class="button"
        @click="createPost"
    >Создать</button>
  </form>
</template>

<script>
export default {
  name: "PostForm",
  data() {
    return {
      post: {
        title: '',
        body:  '',
      }
    }
  },
  methods:{
    createPost() {
      this.post.id = Date.now();
      this.$emit('create', this.post)
      this.post ={
        title: '',
        body:  '',
      }
    },
  }
}
</script>

<style scoped>

form {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.input {
  width: 100%;
  border: 1px solid teal;
  padding: 10px 15px;
  margin: 10px 10px;
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

.title{
  color: white;
  padding: 10px 15px;
  border: 1px dashed white;
}

</style>