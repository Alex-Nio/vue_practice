<template>
  <div class="full-wrapper">
    <header>
      <header-nav></header-nav>
      <router-view />
    </header>
    <div class="container">
      <div class="content">
        <h1 class="title">{{ Title }}</h1>
        <post-form @create="createPost"></post-form>
        <post-list :posts="posts"></post-list>
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
