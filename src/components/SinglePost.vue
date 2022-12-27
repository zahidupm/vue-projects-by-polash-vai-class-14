<template>
  <li>
    <div style="display: inline-block" :class="{ fav: post.fav }">
      {{ post.name }}
    </div>
    | <button @click="handleDelete(post)">Delete Post</button> |
    <button @click="$emit('fav', post)">Fav Post</button>
  </li>
</template>

<script>
export default {
  name: "SinglePost",
  methods: {
    handleDelete(post) {
      this.$emit("delete", post);
    },
  },
  props: {
    post: {
      type: Object,
    },
  },
};
</script>

<style scoped>
.fav {
  color: green;
}
</style>
