<template>
  <h1 class="text-3xl text-red-400">{{ message }}</h1>
  <button @click="addPost">Add Post</button>
  Name: {{ name }}
  <ul>
    <SinglePost
      v-for="post in posts"
      :post="post"
      :key="post.id"
      @delete="handleDelete"
      @fav="handleFav"
    ></SinglePost>
  </ul>
</template>

<script>
import Number from "../components/Number.vue";
import SinglePost from "../components/SinglePost.vue";

export default {
  name: "HomePage",
  components: { Number, SinglePost },
  computed: {
    name() {
      return `${this.first} ${this.last}`;
    },
  },
  data() {
    return {
      message: "Hello Bangladesh",
      posts: [
        {
          id: 1,
          name: "Jamuna",
          fav: true,
        },
        {
          id: 2,
          name: "Setu",
          fav: false,
        },
        {
          id: 3,
          name: "1996",
          fav: true,
        },
      ],
      first: "Zahid",
      last: "Hasan",
    };
  },
  methods: {
    handleDelete(post) {
      this.posts = this.posts.filter((p) => p.id !== post.id);
    },
    addPost() {
      this.posts.push({
        id: this.posts.length + 1,
        name: `Jamuna ${this.posts.length + 1}`,
      });
    },
    handleFav(post) {
      this.posts = this.posts.map((p) => {
        if (p.id === post.id) {
          p.fav = !p.fav;
        }
        return p;
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
