<template>
  <md-button class="md-icon-button md-dense" id="undo" @click="clickUndo">
  <md-icon>undo</md-icon> 
  </md-button>
</template>

<script>
import { mapGetters, mapActions } from 'vuex'

export default {
  name: 'AjoutScore',
  data () {
    return {
      valeur: null
    }
  },
  computed: mapGetters(['nomJoueurCourant']),
  methods: {
    ...mapActions(['retirerScore']),
    clickUndo () {
      this.retirerScore()
      this.$root.$emit('resetScore')
    },
  }
}
</script>

<style scoped lang="scss">
</style>
