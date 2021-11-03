<template>
  <div>{{ joke }}</div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      joke: {},
    };
  },
  async created() {
    try {
       const config = {
        headers: { Accept: "application/json" },
      };
      const { data } = await axios.get(
        `https://icanhazdadjoke.com/j/${this.$route.params.id}`,
        config
      );
      this.joke = data.joke;
      console.log(data);
      debugger
    } catch (error) {
      console.log(error.message);
    }
  },
};
</script>

<style>
</style>