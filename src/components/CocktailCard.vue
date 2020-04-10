<template>
    <v-card class="overflow-hidden card-outter" dark color="grey" height="420px">
        <v-row no-gutters>
            <v-col cols="4">
                <v-img :src="cocktail.src" max-height="420px"></v-img>
            </v-col>
            <v-col cols="8">
                <v-card-title class="secondary display-1">{{cocktail.name}}</v-card-title>
                <v-card-subtitle class="accent title">{{cocktail.description}}</v-card-subtitle>
                <v-card-text>Zutaten: <br /> - {{cocktail.incredients}}</v-card-text>
                <v-card-actions class="card-actions">
                <v-btn small height="130px" width="200px" @click="$vuetify.goTo('#top',{
                    duration: 400,
                    offset: 0,
                    easing: 'easeInOutCubic'
                    })"><v-icon dark>mdi-arrow-up</v-icon></v-btn>
                </v-card-actions>
            </v-col>
        </v-row>
    </v-card>
</template>

<script>
    export default {
        name: "CocktailCard",
        props: [ "cocktail" ]
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
</style>
