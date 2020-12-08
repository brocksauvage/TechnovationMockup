<template>
  <b-col class="mb-5">
    <b-nav-item :href="'#'+title">
      <b-card class="nav-card">
        <b-card-text>
          <p><b>{{ title }}</b></p>
          <b-icon :icon="iconName" font-scale="4"/>
          <p> {{ description }} </p>
        </b-card-text>
      </b-card>
    </b-nav-item>
  </b-col>
</template>

<script>
export default {
  title: 'SectionNav',
  color: "#FFFFFF",
  iconName: "patch-question-fll",
  description: "Descriptoin",
  props: {
    title: String,
    color: String,
    iconName: String,
    description: String
  },
  methods: {
    scrollIntoView(evt) {
        evt.preventDefault()
        const href = evt.target.getAttribute('href')
        const el = href ? document.querySelector(href) : null
        if (el) {
          this.$refs.content.scrollTop = el.offsetTop
        }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .nav-card{
    text-align: center;
    border-color: green;
    border-width: 0px;
    font-size: 20px;
    color: #43b12b;
    transition: transform .2s;
  }
  .nav-card:hover{
    transform: scale(1.1);
  }
</style>
