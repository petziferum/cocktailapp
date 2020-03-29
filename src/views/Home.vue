<template>
  <div class="home">
    <v-carousel>
      <v-carousel-item
              v-for="(item,i) in items"
              :key="i"
              :src="item.src"
              reverse-transition="fade-transition"
              transition="fade-transition"
      ></v-carousel-item>
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
