<template>
  <v-app>
    <v-app-bar
      app
      color="blue-grey darken-3"
      dark
      class="navbarTop"
    >
      <div class="d-flex align-center">
        <v-img
          alt="covid-19 logo"
          class="shrink mr-2"
          contain
          src="@/assets/logo.png"
          transition="scale-transition"
          width="40"
        />
        <h1 class="navbarTitle">COVID-19 statistics</h1>
      </div>
    </v-app-bar>

    <v-content>
      <HelloWorld/>
    </v-content>
  </v-app>
</template>

<script>
import HelloWorld from './components/HelloWorld';

export default {
  name: 'App',

  components: {
    HelloWorld,
  },

  data: () => ({
    //
  }),
};
</script>

<style>

.navbarTitle{
  font-family: 'Montserrat', sans-serif;
  font-size: 20px;
  font-weight: bold;
}
.navbarTop{
  /* background-image: url(https://i.imgur.com/Pa1MxLp.png);
  background-size: 300px;
  color: rgba(255, 255, 255, 0.26); */
}
</style>
