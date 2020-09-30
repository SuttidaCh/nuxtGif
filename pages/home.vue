<template>
  <div class="container">
    <v-col justify="center" align="center">
      <v-col cols="6" sm="4" md="5">
        <v-text-field
          v-model="keyword"
          type="text"
          placeholder="Search"
          solo
        ></v-text-field>
        <v-btn color="primary" @click="searchData()"> Search for Gifs </v-btn>
        <p><br /></p>

        <iframe
          width="420"
          height="315"
          src="https://www.youtube.com/embed/gdZLi9oWNZg"
          frameborder="0"
          allowfullscreen
        ></iframe>
      </v-col>
    </v-col>

    <p><br /></p>
    <div class="text-center card overflow-hidden row no-gutters">
      <v-card
        v-for="data in resultData"
        :key="data.id"
        class="mb-5 ml-5"
        style="max-width: 30%"
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
        <v-card-text>{{ data.import_datetime }}</v-card-text>
        <v-btn nuxt to="/detail">More info</v-btn>
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
            '&limit=30&rating=g'
        )
        .then((response) => {
          this.resultData = response.data.data
        })
    },
  },
}
</script>

<style></style>
