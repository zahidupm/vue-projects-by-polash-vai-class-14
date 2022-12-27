<template>
  <li>{{ post.name }} | <button @click="handleDelete">Delete Post</button></li>
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

<style scoped></style>
