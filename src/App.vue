<template>
  <div id='app'>
  <h1>Beers</h1>
  <beers-list :beers = "beers" ></beers-list>
  </div>
</template>

<script>
import BeersList from './components/BeersList.vue';
import {eventBus} from "./main.js"

export default {
  name: "app",
  data() {
    return {
      beers: [],
      selectedBeer: null
    }
  },
  mounted(){
    fetch('https://api.punkapi.com/v2/beers')
    .then(res => res.json())
    .then(beers => this.beers = beers)

    eventBus.$on('beer-selected', (beer) => {
      this.selectedBeer = beer
      console.log('checking eventbus on', beer)
    })
  },
  
  components: {
    'beers-list': BeersList
  } 
}
</script>

<style>

</style>