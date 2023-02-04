<template>
  <form class="posts-form" @submit.prevent>
    <h1 class="form-title">Создание поста</h1>
    <input
      v-model="post.title"
      class="input"
      type="text"
      placeholder="Описание"
    />
    <input
      v-model="post.body"
      class="input"
      type="text"
      placeholder="Название"
    />
    <button @click="createPost" class="btn form-btn">Создать</button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      post: {
        title: "",
        body: "",
      },
    };
  },
  methods: {
    createPost() {
      this.post.id = Date.now();
      this.$emit("create", this.post);
      this.post = {
        title: "",
        body: "",
      };
    },
  },
};
</script>

<style lang="scss" scoped>
@import "../assets/scss/imports.scss";
.posts-form {
  @include fdc;

  padding: 15px 0;
}

.form-title {
  margin-bottom: 20px;
}

.input {
  width: 100%;
  border: 1px solid teal;
  padding: 15px 20px;
  margin: 10px 0;
}

.btn {
  cursor: pointer;
  margin-top: 15px;
  align-self: flex-end;
  padding: 10px 15px;
  background: none;
  color: teal;
  border: 1px solid teal;
}
</style>
