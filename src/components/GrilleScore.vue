<template>
  <div class="grilleScore">
    <md-table md-card>
      <md-table-row>
        <md-table-head v-for="joueur in listeJoueurs" :key="joueur.id">
          {{ joueur.nom }}
        </md-table-head>
      </md-table-row>
      <md-table-row>
        <md-table-cell class="total" md-numeric v-for="joueur in listeJoueurs" :key="joueur.id">
          {{ joueur.listeScore.reduce((somme, valeur) => valeur + somme, 0) }}
        </md-table-cell>
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

<style lang="scss">
.md-table-head-container {
  text-align: center;
}
.md-table-cell.md-numeric {
  padding: right 10px;
}
.total {
  font-weight: bold;
}
</style>
