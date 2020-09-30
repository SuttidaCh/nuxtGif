<template>
  <div>
    <h1>Shop page</h1>
    <ul>
      <li v-for="i in 15" :key="i">
        สินค้าหมายเลข {{ i }}
        <nuxt-link
          :to="{
            name: 'Shop-id',
            params: { id: i },
          }"
          >รายละเอียด</nuxt-link
        >
      </li>
    </ul>
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
export default {}
</script>
<style></style>
