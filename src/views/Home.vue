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
              v-for="(item,i) in cocktails"
              :key="i"
              class="carousel"
              style="cursor:pointer"
              @click="checkCocktail(item)"
              >

        <v-img :src="item.src" height="90%"  contain><v-card-title class="white--text display-3 font-weight-medium d-flex justify-center pt-10">{{item.name}}</v-card-title></v-img>
      </v-carousel-item>
    </v-carousel>
    <v-container v-show="show">
      <v-row>
        <div style="height: 3000px"></div>
      </v-row>
      <v-row>
        <v-col>
          <section id="cocktail">
            <v-expand-transition>
            <app-cocktail-card :cocktail="cocktail" @up="goUp"></app-cocktail-card>
            </v-expand-transition>
          </section>
        </v-col>
      </v-row>
    </v-container>

  </div>
</template>

<script>
import appCocktailCard from '@/components/CocktailCard'

export default {
  name: 'Home',
  components: {
    appCocktailCard
  },
  data () {
    return {
      cocktails: [
        { src: require('@/assets/blue.jpg'), name:"Schwimmbad Pisse",description:"Blau und süffig.", incredients:["Rum", "Pipi", "spucke", "wasser", "Rum"]},
        {src: require('@/assets/green.jpg'), name:"Corona Schlotz",description:"grün und klebrig.", incredients:["Absynth", "Pipi", "spucke", "wasser", "cola"]},
        {src: require('@/assets/red.jpg'), name:"Nasenbluten",description:"Blutrot und bitter.", incredients:["Blut", "Pipi", "spucke", "Wodka", "Motoröl"]},
        {src: require('@/assets/whisky.jpg'), name:"Einfach n Whisky",description:"Was gibts an 'Einfach Whisky' nicht zu verstehen?", incredients:["Whisky"]},
      ],
      cocktail: [
    {
      name:"Cocktailname",
      description:"Beschreibung",
      Incredients:"Zutaten",
      src: "",
    }
    ],
      showstatus: false,
      working: false
  }
  },
  methods: {
    checkCocktail(item) {
      this.showstatus = true
      this.cocktail = item
      this.$vuetify.goTo('#cocktail', this.options)
    },
    goUp() {
      this.$vuetify.goTo('#top', {
        duration: 400,
        offset: 0,
        easing: 'easeInOutCubic'
      })
      setTimeout(
        this.setfalse
      , 500)
    },
    setfalse() {
      console.log(this.show)
      this.showstatus = false
    },
  },
  computed: {
    options() {
      return {
        duration: 400,
        offset: 0,
        easing: 'easeInOutCubic'
      }
    },
    show () {
      console.log(this.showstatus)
      return this.showstatus
    }

  }
}
</script>
<style>
.carousel {
  background-color: black;
}
</style>
