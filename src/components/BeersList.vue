<template>
<div>
  <ul>
      <li v-for='(beer, index) in beers' :beer='beer' :key=index></li>
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
    },
}
</script>

<style>

</style>