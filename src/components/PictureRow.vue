<template>
  <b-row class="justify-content-center my-5">
    <b-col v-if="label" col md="2" class="my-auto">
      <p class="mb-0 font-weight-bold text-right">{{label}}</p>
    </b-col>
    <b-col v-for="pic in pictures" :key="pic" col md="4" class="my-auto">
      <b-img :src="'https://lh3.googleusercontent.com/'+pic" fluid></b-img>
    </b-col>
  </b-row>
</template>

<script>
export default {
  pictures: [],
  label: null,
  props: {
    pictures: Array,
    label: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
