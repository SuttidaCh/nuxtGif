<template>
  <div class="container">
    <v-col justify="center" align="center">
      <v-col cols="6" sm="4" md="5">
        <v-img
          src="https://media.giphy.com/media/o0vwzuFwCGAFO/giphy.gif"
          class="rounded-circle"
          max-width="230"
        />
        <p><br /></p>
        <v-text-field
          v-model="keyword"
          type="text"
          placeholder="Search"
          solo
        ></v-text-field>
        <v-btn color="#9F693E" @click="searchData()"> Search for Gifs </v-btn>
        <p><br /></p> </v-col
    ></v-col>
    <v-col justify="center" align="center">
      <iframe
        width="420"
        height="315"
        src="https://www.youtube.com/embed/gdZLi9oWNZg"
        frameborder="0"
        allowfullscreen
      ></iframe>
    </v-col>
    <p><br /></p>
    <div class="text-center card overflow-hidden row no-gutters">
      <v-card
        v-for="data in resultData"
        :key="data.id"
        color="#F6EEE0"
        class="mb-5 ml-5"
        max-width="350"
      >
        <v-card-text
          :key="data.id"
          justify="center"
          class="headline font-weight-bold"
        >
          {{ data.title }}
        </v-card-text>
        <video
          :key="data.id"
          class="rounded"
          type="video"
          :src="data.images.original.mp4"
          autoplay=""
          loop=""
          style="max-width: 100%"
        ></video>
        <v-btn
          color="#FAFAFA"
          nuxt
          :to="{
            name: 'detail-id',
            params: {
              id: data.id,
              title: data.title,
              rating: data.rating,
              import_datetime: data.import_datetime,
              type: data.type,
              video: data.images.original.mp4,
              username: data.username,
              url: data.url,
            },
          }"
          >More info</v-btn
        >
        <p><br /></p>
      </v-card>
    </div>
  </div>
</template>
<script>
import axios from 'axios'
export default {
  data() {
    return {
      resultData: null,
      keyword: '',
    }
  },
  methods: {
    searchData() {
      axios
        .get(
          'https://api.giphy.com/v1/gifs/search?api_key=39vI8skUqOzHnLMOJZiRkLKJ7SIWbQ4J&q=' +
            this.keyword +
            '&limit=30'
        )
        .then((response) => {
          this.resultData = response.data.data
        })
        .catch((err) => {
          // eslint-disable-next-line no-console
          console.log(err)
        })
    },
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
