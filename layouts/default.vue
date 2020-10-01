<template>
  <v-app>
    <v-app-bar :clipped-left="clipped" fixed app color="#BCAE90">
      <v-toolbar-title v-text="title" />
      <v-spacer />
      <v-btn class="ma-1" outlined colors="indigo" to="/home">Home</v-btn>
    </v-app-bar>
    <v-main>
      <v-container>
        <nuxt />
      </v-container>
    </v-main>
    <v-footer :absolute="!fixed" app>
      <span>&copy; HBD TO PARK JIMIN BTS 🌈🌈🌈</span>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  data() {
    return {
      clipped: false,
      drawer: false,
      fixed: false,
      miniVariant: false,
      right: true,
      title: 'Giphy',
    }
  },
}
</script>
