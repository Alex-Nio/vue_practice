<template>
  <div class="full-wrapper">
    <header>
      <header-nav></header-nav>
      <router-view />
    </header>
    <div class="container">
      <div v-if="posts.length > 0" class="content">
        <h1 class="title">{{ Title }}</h1>
        <post-form @create="createPost"></post-form>
        <post-list :posts="posts" @remove="removePost"></post-list>
      </div>
      <div v-else>
        <h3>Список постов пуст</h3>
      </div>
    </div>
  </div>
</template>

<script>
import HeaderNav from "@/components/HeaderNav";
import PostList from "@/components/PostList";
import PostForm from "@/components/PostForm";

export default {
  components: {
    HeaderNav,
    PostList,
    PostForm,
  },
  data() {
    return {
      Title: "Заголовок",
      posts: [
        { id: 1, title: "Пост 1", body: "Описание поста 1" },
        { id: 2, title: "Пост 2", body: "Описание поста 2" },
        { id: 3, title: "Пост 3", body: "Описание поста 3" },
      ],
    };
  },
  methods: {
    createPost(post) {
      this.posts.push(post);
    },
    removePost(post) {
      this.posts = this.posts.filter((p) => p.id !== post.id);
    },
  },
};
</script>

<style lang="scss" scoped>
@import "./assets/scss/imports.scss";

.title {
  font-size: 2rem;
}

.content {
  padding: 20px 0;
}

.posts {
  width: 100%;
  margin-top: 20px;
}
</style>
