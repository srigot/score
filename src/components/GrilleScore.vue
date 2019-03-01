<template>
  <div class="grilleScore">
    <md-table>
      <md-table-row>
        <md-table-head v-for="joueur in listeJoueurs" :key="joueur.id">
          {{ joueur.nom }}
        </md-table-head>
      </md-table-row>
      <md-table-row>
        <md-table-head md-numeric v-for="joueur in listeJoueurs" :key="joueur.id">
          {{ joueur.listeScore.reduce((somme, valeur) => valeur + somme, 0) }}
        </md-table-head>
      </md-table-row>
      <md-table-row>
        <md-table-cell md-numeric v-for="joueur in listeJoueurs" :key="joueur.id">
          <div v-for="(score, index) in joueur.listeScore" :key="index">{{ score }}</div>
        </md-table-cell>
      </md-table-row>
    </md-table>
  </div>
</template>

<script>
import { mapState } from 'vuex'

export default {
  name: 'GrilleScore',
  computed: mapState(['listeJoueurs'])
}
</script>

<style scoped lang="scss">
</style>
