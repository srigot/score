<template>
  <div v-if="nomJoueurCourant !== ''" class="ajoutScore">
    <div class="md-layout md-gutter">
      <div class="md-layout-item">Joueur : {{ nomJoueurCourant }}</div>
      <div class="md-layout-item">
        <md-field>
          <label>Score</label>
          <md-input v-model.number="valeur" type="number" size="4" number @keyup.enter.native="validerSaisie" ref="score"></md-input>
        </md-field>
      </div>
      <div class="md-layout-item">
        <md-button id="undo" @click="clickUndo">Undo</md-button>
      </div>
    </div>
  </div>
  <div v-else>
    <md-snackbar md-duration="Infinity" active.sync="true" md-persistent>
      <span>Pas de partie en cours</span>
      <md-button class="md-primary" to="/new">Nouvelle partie</md-button>
    </md-snackbar>
  </div>
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
    this.$refs.score.$el.focus()
  },
  computed: mapGetters(['nomJoueurCourant']),
  methods: {
    ...mapActions(['ajouterScore', 'retirerScore']),
    resetCompteurs () {
      this.valeur = null
    },
    validerSaisie () {
      let score = this.valeur
      this.ajouterScore(score)
      this.resetCompteurs()
    },
    clickUndo () {
      this.retirerScore()
      this.resetCompteurs()
      this.$refs.score.$el.focus()
    },
  }
}
</script>

<style scoped lang="scss">
</style>
