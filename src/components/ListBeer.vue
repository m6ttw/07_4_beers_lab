<template>
  <div>
  <li v-on:click= {{beer.name}}> </li>
  </div>
</template>

<script>
export default {
    name: "list-beer",
    props: ["beer"]
}
</script>

<style>

</style>