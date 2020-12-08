<template>
  <b-col class="mb-5">
    <b-overlay :show="show" rounded="sm" @shown="onShown" @hidden="onHidden">
      <b-card class="term-card" :style="styleObject" :aria-hidden="show ? 'true' : null">
        <b-card-text ref="show" :disabled="show" variant="primary" @click="show = true">
          <p><b>{{ term.title }}</b></p>
          <b-icon :icon="term.iconName" font-scale="3"/>
        </b-card-text>
      </b-card>
      <template #overlay>
        <div class="text-center">
          <p id="cancel-label">{{term.description}}</p>
          <b-button
            ref="cancel"
            variant="outline-danger"
            size="sm"
            aria-describedby="cancel-label"
            @click="show = false"
          >
            Cancel
          </b-button>
        </div>
      </template>
    </b-overlay>
  </b-col>
</template>

<script>
export default {
  term: {},
  props: {
    term: Object
  },
  data() {
      return {
        show: false
      }
  },
  methods: {
    onShown() {
      // Focus the cancel button when the overlay is showing
      this.$refs.cancel.focus()
    },
    onHidden() {
      // Focus the show button when the overlay is removed
      this.$refs.show.focus()
    }
  },
  computed: {
    styleObject: function() {
      return {
        '--border-color': this.term.color
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .term-card{
    text-align: center;
    border-width: 3px;
    border-color: var(--border-color);
    transition: color 0.5s;
  }
  .term-card:hover{
    color: var(--border-color);
    transition: color 0.5s;
  }
</style>
