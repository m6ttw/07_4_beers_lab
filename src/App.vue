<template>
  <div id='app'>
  <h1>Beers</h1>
  <beers-list :beers = "beers" ></beers-list>
  <beer-detail :beer = 'beer' favouriteBeers: = 'favouriteBeers'></beer-detail>
  <h2>Here are your favourites!</h2>
  <ul>
    <li v-for='beer in favouriteBeers' :key="beer">{{beer.name}}</li>
  </ul> 
  <!-- <list-beer :beer = 'beer' favouriteBeers: = 'favouriteBeers'></list-beer> -->

  </div>
</template>

<script>
import BeersList from './components/BeersList.vue';
import {eventBus} from "./main.js"
import BeerDetail from './components/BeerDetail.vue'
// import ListBeer from './components/ListBeer.vue'

export default {
  name: "app",
  data() {
    return {
      beers: [],
      beer: null,
      favouriteBeers: []
    }
  },
  mounted(){
    fetch('https://api.punkapi.com/v2/beers')
    .then(res => res.json())
    .then(beers => this.beers = beers)

    eventBus.$on('beer-selected', (beer) => {
      this.beer = beer
      // console.log('checking eventbus on', beer)

    eventBus.$on("favourite-beer-selected", (beer) => {
      this.addFavouriteBeer()
      console.log('addfavouritebeer in app.vue: ', this.beer)
     })
    })
  },
  methods: {
    addFavouriteBeer () {
      if (!this.favouriteBeers.includes(this.beer))
      {this.favouriteBeers.push(this.beer)}
    }
  },
  components: {
    'beers-list': BeersList,
    'beer-detail': BeerDetail,
    // 'list-beer': ListBeer
  }
}
</script>

<style lang='css' scoped>
#app {
display: flex
}

</style>