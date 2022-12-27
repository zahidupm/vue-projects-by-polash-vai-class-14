<template>
  <h1 class="text-3xl text-red-400">{{ message }}</h1>
  <button @click="addPost">Add Post</button>
  <ul>
    <SinglePost
      v-for="post in posts"
      :post="post"
      :key="post.id"
      @delete="handleDelete"
    ></SinglePost>
  </ul>
</template>

<script>
import Number from "../components/Number.vue";
import SinglePost from "../components/SinglePost.vue";

export default {
  name: "HomePage",
  components: { Number, SinglePost },
  data() {
    return {
      message: "Hello Bangladesh",
      posts: [
        {
          id: 1,
          name: "Zahid",
        },
        {
          id: 2,
          name: "Hasan",
        },
      ],
    };
  },
  methods: {
    handleDelete($post) {
      this.posts = this.posts.filter((post) => post.id !== $post.id);
    },
    addPost() {
      this.posts.push({
        id: this.posts.length + 1,
        name: `Limon ${this.posts.length + 1}`,
      });
    },
  },
};
</script>

<style scoped>
h1 {
  color: green;
}
</style>
