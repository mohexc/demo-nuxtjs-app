<template>
  <div>
    <Joke 
    v-for="joke in jokes" 
    v-bind:key="joke.id"  
    v-bind:id="joke.id"
    v-bind:joke="joke.joke"
    />
  </div>
</template>

<script>
import axios from "axios";
import Joke from "../../components/Joke.vue";

export default {
  components: {
    Joke,
  },
  data() {
    return {
      jokes: [],
    };
  },
  async created() {
    try {
      const config = {
        headers: { Accept: "application/json" },
      };
      const { data } = await axios.get(
        "https://icanhazdadjoke.com/search",
        config
      );
      this.jokes = data.results;
    } catch (error) {
      console.log(error.message);
    }
  },
  head() {
    return {
      title: "Dad Jokes",
      meta: [
        {
          hid: "description",
          name: "description",
          content: "Best place for corny dad jokes",
        },
      ],
    };
  },
};
</script>

<style>
</style>