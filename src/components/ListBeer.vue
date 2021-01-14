<template>
  <div>
  <li v-on:click="handleClick">{{beer.name}}</li>
  <!-- <input type="checkbox" v-on:click="addFavouriteBeer" id='favourite' name='favourite' value='Choose a favourite beer' > -->

  </div>
</template>

<script>
import {eventBus} from '../main.js'

export default {
    name: "list-beer",
    props: ["beer", "favouriteBeers"],
    methods: {
        handleClick() {
            eventBus.$emit('beer-selected', this.beer)
            // if (this.beer != null) 
            // console.log(beer, this.beer);
        }
    }
}
</script>

<style>

</style>