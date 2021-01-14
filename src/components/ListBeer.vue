<template>
  <div>
  <li v-on:click="handleClick">{{beer.name}} </li>
  </div>
</template>

<script>
import {eventBus} from '../main.js'

export default {
    name: "list-beer",
    props: ["beer"],
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