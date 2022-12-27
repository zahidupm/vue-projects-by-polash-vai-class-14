<template>
  <button @click="addPost">Add Post</button>
  <!-- favCount: {{ favCount }} <br />
  UnFavorite Count: {{ unFavCount }} -->
  <h1>All</h1>
  <ul>
    <SinglePost
      v-for="post in posts"
      :post="post"
      :key="post.id"
      @delete="handleDelete"
      @fav="handleFav"
    ></SinglePost>
  </ul>
  <br />
  <h1>Favs</h1>
  <ul>
    <SinglePost
      v-for="post in favs"
      :post="post"
      :key="post.id"
      @delete="handleDelete"
      @fav="handleFav"
    ></SinglePost>
  </ul>
  <br />
  <h1>UnFavs</h1>
  <ul>
    <SinglePost
      v-for="post in unFavs"
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
    favs() {
      return this.posts.filter((post) => post.fav);
    },
    unFavs() {
      return this.posts.filter((post) => !post.fav);
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
