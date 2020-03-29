<template>
  <div class="home">
    <v-carousel
            height="420px"
            hide-delimiter-background
            delimiter-icon="mdi-glass-cocktail"
            cycle
            dark
    >
      <v-carousel-item
              v-for="(item,i) in items"
              :key="i"
              class="carousel"

      >
          <v-img :src="item.src" height="100%" contain></v-img>

      </v-carousel-item>
    </v-carousel>
  </div>
</template>

<script>
// @ is an alias to /src


export default {
  name: 'Home',
  data () {
    return {
      items: [
        { src: require('@/assets/blue.jpg')},
        {src: require('@/assets/green.jpg')},
        {src: require('@/assets/red.jpg')},
        {src: require('@/assets/whisky.jpg')},
      ]
    }

  }
}
</script>
<style>
.carousel {
  background-color: black;
}
</style>