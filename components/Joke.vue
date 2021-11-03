<template>
<nuxt-link :to="'jokes/'+id" >
  <div class="joke">
    <p>{{ joke }}</p>
  </div>
  </nuxt-link>
</template>

<script>
export default {
  name: "Joke",
  props: ["joke", "id"],
};
</script>

<style>
.joke {
  padding: 2rem;
  border: 1px dotted #ccc;
  margin: 1rem 0;
}
</style>