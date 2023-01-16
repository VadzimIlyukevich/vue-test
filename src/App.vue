<script>
export default {
  data() {
    return {
      posts: [
        {id: 1, title: 'JavaScript', body: 'ТОП'},
        {id: 2, title: 'Python', body: 'ТОП'},
        {id: 3, title: 'C++', body: 'ТОП'},
      ]
    }
  },
  methods: {
    addLike() {
      this.likes += 1
    },
    addDislike() {
      this.dislikes += 1
    }
  }
}
</script>

<template>
  <div class="app">
    <form>
      <input class="input" type="text" placeholder="Название">
      <input class="input" type="text" placeholder="Описание">
      <button class="button">Создать</button>
    </form>
    <div>
      <div class="post" v-for="post in posts">
        <div><strong>Название: {{ post.title }}</strong> {{ post.body }}</div>
        <div><strong>Описание:</strong> {{ post.title }} {{ post.body }}</div>
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
