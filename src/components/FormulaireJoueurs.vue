<template>
  <div class="formulaireJoueurs container">
    <div>
    </div>
    <div>
      <form class="md-layout" @submit="onSubmit">
        <md-card class="md-layout-item md-size-50 md-small-size-100">
          <md-card-header>
            <md-field>
              <label for="nb">Nombre de joueurs</label>
              <md-select v-model="nbJoueurs" name="nb" id="nb" @md-selected="updateNomsJoueurs">
                <md-option value=1>1 Joueur</md-option>
                <md-option value=2>2 Joueurs</md-option>
                <md-option value=3>3 Joueurs</md-option>
                <md-option value=4>4 Joueurs</md-option>
                <md-option value=5>5 Joueurs</md-option>
                <md-option value=6>6 Joueurs</md-option>
                <md-option value=7>7 Joueurs</md-option>
                <md-option value=8>8 Joueurs</md-option>
              </md-select>
            </md-field>
          </md-card-header>

          <md-card-content>
            <md-field v-for="(joueur, index) in joueurs" :key="index">
              <label for="first-name">{{listePlaceHolder[index]}}</label>
              <md-input v-model="joueurs[index]" required/>
            </md-field>
          </md-card-content>

          <md-card-actions>
            <md-button type="submit" class="md-primary">Valider</md-button>
          </md-card-actions>
        </md-card>
      </form>
    </div>
  </div>
</template>

<script>
import { mapActions } from 'vuex'

export default {
  name: 'FormulaireJoueurs',
  data () {
    return {
      joueurs: [],
      nbJoueurs: 2,
      listePlaceHolder: []
    }
  },
  methods: {
    ...mapActions(['creerNouvellePartie']),
    ajouterJoueur () {
      this.listePlaceHolder.push(`Joueur ${this.listePlaceHolder.length + 1}`)
      this.joueurs.push('')
    },
    supprimerJoueur () {
      this.joueurs.pop()
      this.listePlaceHolder.pop()
    },
    updateNomsJoueurs() {
      while (this.joueurs.length > this.nbJoueurs) {
        this.supprimerJoueur()
      }
      while (this.joueurs.length < this.nbJoueurs) {
        this.ajouterJoueur()
      }
    },
    onSubmit () {
      this.creerNouvellePartie(this.joueurs).then(() => {
        this.$router.push('/')
      })
    }
  }
}
</script>

<style scoped lang="scss">
button {
  margin-left: 2px
}
.row {
  margin-bottom: 2px
}
</style>
