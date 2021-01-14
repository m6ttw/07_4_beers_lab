<template>
<div>
  <ul>
      <list-beer v-for='(beer, index) in beers' :beer='beer' :key=index></list-beer>
  </ul>    
</div>
</template>

<script>
import ListBeer from "./ListBeer.vue"

export default {
    name: 'beers-list',
    props: ['beers'],

    components: {
        'list-beer': ListBeer
    }
}
</script>

<style>
    ul {
  list-style-type: none;
}
</style>