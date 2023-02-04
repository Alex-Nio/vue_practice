<template>
  <div class="posts" v-for="post in posts">
    <div class="post">
      <div>
        <strong>Название:</strong>
        {{ post.title }}
      </div>
      <div>
        {{ post.body }}
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    posts: {
      type: Array,
      required: true,
    },
  },
};
</script>

<style lang="scss" scoped>
@import "../assets/scss/imports.scss";
.post {
  @include fdcjc_ais;
  font-size: 1.4rem;
  padding: 20px;
  margin: 10px 0;
  border: 2px solid teal;
}
</style>
