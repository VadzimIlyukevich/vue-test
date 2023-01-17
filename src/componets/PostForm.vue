<template>
  <form @submit.prevent>
    <h4 class="title">Создание поста</h4>
    <PostInput
        placeholder="Название"
           v-model="post.title"
    />

    <PostInput
        placeholder="Описание"
        v-model="post.body"
    />

    <PostButton
        class="submit"
        @click="createPost"
    >
      Создать
    </PostButton>
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

.title{
  color: white;
  padding: 10px 15px;
  border: 1px dashed white;
}

.submit{
  align-self: flex-end;
}

</style>