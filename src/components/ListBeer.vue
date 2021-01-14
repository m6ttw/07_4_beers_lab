<template>
  <div>
  <li v-on:click="handleClick">{{beer.name}} </li>
  </div>
</template>

<script>
export default {
    name: "list-beer",
    props: ["beer"],
    methods: {
        handleClick() {
            if (this.beer != null) 
            {}
        }
    }
}
</script>

<style>

</style>