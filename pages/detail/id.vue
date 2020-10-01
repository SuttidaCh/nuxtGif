<template>
  <div class="text-center card overflow-hidden">
    <v-col justify="center" align="center">
      <v-card color="" class="mb-6 ml-6" max-width="350">
        <video
          class="rounded"
          type="video"
          :src="gif.video"
          autoplay=""
          loop=""
          style="max-width: 100%"
        ></video>
        <h2>Detail</h2>
        <h3>ID : {{ gif.id }}</h3>
        <h3>Title : {{ gif.title }}</h3>
        <h3>type : {{ gif.type }}</h3>
        <h3>rating : {{ gif.rating }}</h3>
        <h3>username : {{ gif.username }}</h3>
        <h3>date : {{ gif.import_datetime }}</h3>
        <p><br /></p>
        <v-btn color="#7F684A" :href="gif.url"> Go somewhere </v-btn>
        <p><br /></p>
      </v-card>
    </v-col>
  </div>
</template>
<script>
export default {
  data() {
    return {
      gif: this.$route.params,
    }
  },
}
</script>
<style>
#app {
  background-image: url(https://rawpixel-live.imgix.net/collection/cover/99bf1f74fb0cfc223e186b946c7135dd_cover.png?auto=&bg=transparent&con=3&cs=srgb&dpr=1&fit=clip&fm=png&h=1200&ixlib=php-3.1.0&q=65&usm=15&vib=3&w=1200&s=79575b05cb7a0c3f94e7fde28060a873);
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  margin-top: 60px;
}
</style>
