<template>
  <form @submit.prevent>
    <input class="input"
           type="text"
           placeholder="Название"
           @input="post.title = $event.target.value"
           v-bind:value="post.title"
    >

    <input class="input"
           type="text"
           placeholder="Описание"
           @input="post.body = $event.target.value"
           v-bind:value="post.body"
    >

    <button class="button">Создать</button>
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

</style>