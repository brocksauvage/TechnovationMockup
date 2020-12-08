<template>
 <b-col class="mb-3">
   <b-table :items="items"></b-table>
 </b-col>
</template>

<script>
export default {
  title: 'DataTable',
  items: [],
  props: {
    items: Array
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
