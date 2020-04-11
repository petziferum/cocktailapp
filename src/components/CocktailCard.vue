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
                    <v-btn height="130px" width="200px" rounded @click="pourDrink"><v-icon dark>mdi-water-pump</v-icon></v-btn>
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
        props: [ "cocktail" ],
        methods: {
            pourDrink() {
                var Gpio = require('onoff').Gpio; //include onoff to interact with the GPIO
                var LED = new Gpio(4, 'out'); //use GPIO pin 4, and specify that it is output
                var blinkInterval = setInterval(blinkLED, 250); //run the blinkLED function every 250ms

                function blinkLED() { //function to start blinking
                    if (LED.readSync() === 0) { //check the pin state, if the state is 0 (or off)
                        LED.writeSync(1); //set pin state to 1 (turn LED on)
                    } else {
                        LED.writeSync(0); //set pin state to 0 (turn LED off)
                    }
                }

                function endBlink() { //function to stop blinking
                    clearInterval(blinkInterval); // Stop blink intervals
                    LED.writeSync(0); // Turn LED off
                    LED.unexport(); // Unexport GPIO to free resources
                }

                setTimeout(endBlink, 5000); //stop blinking after 5 seconds
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
</style>
