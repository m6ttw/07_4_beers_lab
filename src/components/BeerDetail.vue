<template>
    <div v-if="beer">
        <h3>{{beer.name}}</h3>
        <p>First Brewed: {{beer.first_brewed}}</p>
        <p>ABV: {{beer.abv}}</p>
        <!-- <input type="checkbox" v-model="favouriteChecked" v-if:"favouriteChecked" = true" id='favourite' name='favourite' value='Choose a favourite beer' > -->
        <input type="button" v-on:click="emitFavouriteBeer" id='favourite' name='favourite' value='Add or Remove this beer to your list of favourite!' >
        <!-- <label for='favourite'>Select this as a favourite beer </label> -->
    </div>
</template>

<script>
import {eventBus} from "../main.js"

export default {
    name: "beer-detail",
    data () { 
        return {
        favouriteChecked: null,
    }},
    props: ["beer", "favouriteBeers"], 
    methods: {
        emitFavouriteBeer() {
            eventBus.$emit("favourite-beer-selected", this.beer)
            console.log('emitfavourite: ', this.beer)
        }
    }
}
</script>
<style>

</style>