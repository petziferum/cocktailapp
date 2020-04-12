<template>
    <v-card class="overflow-hidden card-outter bg" dark elevation="9" shaped color="grey" height="420px"
            :style="{ 'background-image': 'url(' + background + ')' }"
    ><v-container class="pa-0" full-width>
        <v-row no-gutters>
            <v-col cols="4">
                <v-img :src="cocktail.src" height="420" max-height="420px"></v-img>
            </v-col>
            <v-col cols="8">
                <v-card-title class="bgtitle">{{cocktail.name}}</v-card-title>
                <v-card-subtitle class="mt-0 desc">{{cocktail.description}}</v-card-subtitle>
                <v-card light width="100%" class="pa-2">   <b> Zutaten:</b>
                    <ul dense v-for="item in cocktail.incredients" :key="item.id">
                        <li dense>{{item}}</li>
                    </ul>
                </v-card>
                <v-card-actions class="card-actions">
                    <v-btn height="120px" width="300px" rounded color="success" @click="ausgabe(cocktail.name)"><v-icon dark>mdi-water-pump</v-icon></v-btn>
                    <v-btn small height="100px" width="180px" rounded @click="$emit('up')"><v-icon dark>mdi-arrow-up</v-icon></v-btn>
                </v-card-actions>
                <v-snackbar multi-line
                        v-model="snackbar"
                >
                    In Zubereitung...
                </v-snackbar>
            </v-col>
        </v-row>
    </v-container>

    </v-card>
</template>

<script>
    export default {
        name: "CocktailCard",
        props: ["cocktail"],
        data() {
            return {
                background: require("@/assets/lowpoly.jpg"),
                working: false
            }
        },
        methods: {
            ausgabe(item) {
                console.log(item, " wird zubereitet!")
                this.working = true
                console.log('working:',this.working)
                setTimeout(this.setWorking, 3000)

            },
            setWorking(){
                this.working = false
            }
        },
        computed: {
            snackbar() {
                console.log('work', this.working)
                return this.working
            }
        }
    }
</script>

<style scoped>
    .card-outter {
        position: relative;
        padding-bottom: 50px;
    }
    .card-actions {
        position: absolute;
        bottom: 0;
        right:0;
    }
    .bg {
        background-size: cover;
    }
    .desc {
        font-size: 1.2rem;
        color:black;
        background-color: rgba(0,0,0,.5);
    }
    .bgtitle {
        font-size: 1.8rem;
        background-color: rgba(0,50,100,.5);
        background-position-x: 0;
        background-position-y: 20%;
        background-size: cover;
    }
</style>
