<template>
  <h1 class="text-3xl text-red-400">{{ message }}</h1>
  <Number></Number>
</template>

<script>
import Number from "../components/Number.vue";

export default {
  name: "HomePage",
  components: { Number },
  data() {
    return {
      message: "Hello Bangladesh",
    };
  },
};
</script>

<style scoped>
h1 {
  color: green;
}
</style>
