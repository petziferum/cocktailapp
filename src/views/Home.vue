<template>
  <div>
    <v-carousel
            id="top"
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
              @click="$vuetify.goTo('#cocktail',options)">

        <v-img :src="item.src" height="90%"  contain><v-card-title class="white--text display-3 font-weight-medium d-flex justify-center pt-10">{{item.name}}</v-card-title></v-img>
      </v-carousel-item>
    </v-carousel>
    <v-container>
      <v-row>
        <div style="height: 1000px"></div>
      </v-row>
      <v-row>
        <v-col>
          <section id="cocktail">
          <v-card dark color="grey" height="420px">
            <v-card-title>Der Cocktail</v-card-title>
            <v-card-subtitle>Der haut rein</v-card-subtitle>
            <v-card-text>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Animi eius fuga id odit qui quidem reiciendis.</v-card-text>
            <v-card-actions>
              <v-btn @click="$vuetify.goTo('#top',options)"><v-icon dark>mdi-arrow-up</v-icon></v-btn>
            </v-card-actions>
          </v-card>
          </section>
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>

<script>
// @ is an alias to /src


export default {
  name: 'Home',
  data () {
    return {
      items: [
        { src: require('@/assets/blue.jpg'), name:"Schwimmbad Pisse"},
        {src: require('@/assets/green.jpg'), name:"Corona Schlotz"},
        {src: require('@/assets/red.jpg'), name:"Nasenbluten"},
        {src: require('@/assets/whisky.jpg'), name:"Einfach n Whisky"},
      ]
    }

  },
  computed: {
    options () {
      return {
        duration: 400,
        offset: 0,
        easing: 'easeInOutCubic'
      }
    }
  }
}
</script>
<style>
.carousel {
  background-color: black;
}
</style>
