<template>
    <v-card class="overflow-hidden card-outter bg" dark elevation="9" shaped color="grey" height="420px"
            :style="{ 'background-image': 'url(' + background + ')' }"
    >
        <v-row no-gutters>
            <v-col cols="4">
                <v-img :src="cocktail.src" height="420px" max-height="420px"></v-img>
            </v-col>
            <v-col cols="8">
                <v-card-title class="secondary display-1">{{cocktail.name}}</v-card-title>
                <v-card-subtitle class="accent title">{{cocktail.description}}</v-card-subtitle>
                <v-card light width="50%">   <b> Zutaten:</b>
                    <ul dense v-for="item in cocktail.incredients" :key="item.id">
                        <li dense>{{item}}</li>
                    </ul>
                </v-card>
                <v-card-actions class="card-actions">
                    <v-btn height="100px" width="300px" rounded color="success"><v-icon dark>mdi-water-pump</v-icon></v-btn>
                <v-btn small height="100px" width="180px" rounded @click="$emit('up')"><v-icon dark>mdi-arrow-up</v-icon></v-btn>
                </v-card-actions>
            </v-col>
        </v-row>
    </v-card>
</template>

<script>
    export default {
        name: "CocktailCard",
        props: ["cocktail"],
        data() {
            return {
                background: require("@/assets/lowpoly.jpg")
            }
        },
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
        background-color: rgba(0,0,0,.5);
        background-position-x: 0;
        background-position-y: 20%;
        background-size: cover;
    }
</style>
