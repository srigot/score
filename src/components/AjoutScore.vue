<template>
  <md-field>
    <label>{{ nomJoueurCourant }}</label>
    <md-input v-model.number="valeur" type="number" size="4" number @keyup.enter.native="validerSaisie" ref="score"></md-input>
  </md-field>
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
  mounted () {
    this.$refs.score.$el.focus(),
    this.$root.$on('resetScore', () => {
      this.resetCompteurs()
    })
  },
  computed: mapGetters(['nomJoueurCourant']),
  methods: {
    ...mapActions(['ajouterScore']),
    resetCompteurs () {
      this.valeur = null
      this.$refs.score.$el.focus()
    },
    validerSaisie () {
      let score = this.valeur
      this.ajouterScore(score)
      this.resetCompteurs()
    },
  }
}
</script>

<style scoped lang="scss">
</style>
