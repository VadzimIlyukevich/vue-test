<script>
export default {
  data() {
    return {
      posts: [
        {id: 1, title: 'JavaScript', body: 'ТОП'},
        {id: 2, title: 'Python', body: 'ТОП'},
        {id: 3, title: 'C++', body: 'ТОП'},
      ],
      title: '',
      body: '',
    }
  },
  methods: {
    createPost(){
      const newPost = {
        id: Date.now(),
        title: this.title,
        body: this.body,
      }
      this.posts.push(newPost);
      this.title = '';
      this.body = '';
    },
  }
}
</script>

<template>
  <div class="app">
    <form @submit.prevent>
      <input class="input"
             type="text"
             placeholder="Название"
             @input="title = $event.target.value"
             v-bind:value="title"
      >

      <input class="input"
             type="text"
             placeholder="Описание"
             @input="body = $event.target.value"
             v-bind:value="body"
      >

      <button class="button" @click="createPost">Создать</button>
    </form>
    <div>
      <div class="post" v-for="post in posts">
        <div><strong>Название:</strong> {{ post.title }}</div>
        <div><strong>Описание:</strong> {{ post.body }}</div>
      </div>
    </div>
  </div>
</template>

<style scoped>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.app{
  padding: 20px ;
}

.post {
  margin-bottom: 5px;
  padding: 15px;
  border: 2px solid teal;
}

form {
  display: flex;
  flex-direction: column;
}

.input {
  width: 100%;
  border: 1px solid teal;
  padding: 10px 15px;
  margin: 10px 0 10px 0;
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
