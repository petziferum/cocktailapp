<template>
  <v-app class="bg">
    <v-content>
      <router-view></router-view>
    </v-content>
  </v-app>
</template>

<script>


export default {
  name: 'App',

  components: {
  },

  data: () => ({
    //
  }),
};
</script>

<style>
  ::-webkit-scrollbar {
    width: 0px;
    background: transparent;
  }
  .bg {
    background-color: #89bc8f;
  }
</style>
