<template lang="html">
  <div class="">
    <h2>{{title}}</h2>
    <img :src="image_url" :alt="title" width="300">
    <p> published by: {{publisher}}</p>
    <p>social rank: {{social_rank}}</p>
    <a :href="f2f_url"> f2f </a>
  </div>
</template>

<script>
export default {
  name: 'Recipe',
  props: {
    publisher: String,
    title: String,
    f2f_url: String,
    social_rank: Number,
    image_url: String,
  }
}
</script>

<style lang="css" scoped>
a {
  text-decoration: none;
  color: #d8412c
}
h2 {
  color: #9d3133
}
</style>
