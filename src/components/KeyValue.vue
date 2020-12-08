<template>
  <b-row class="justify-content-center my-2">
    <b-col col md="2" class="my-auto">
      <p class="highlighted-word mb-0"> {{ name }} </p>
    </b-col>
    <b-col col md="2">
      <b-icon-arrow-right font-scale="3"/>
    </b-col>
    <b-col col md="6" class="my-auto">
      <p class="mb-0">[ {{ items.map(item => item[Object.keys(item)[0]]).join(", ") }} ]</p>
    </b-col>
  </b-row>
</template>

<script>
export default {
  name: "Key",
  items: "Value",
  props: {
    name: String,
    items: Array
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
