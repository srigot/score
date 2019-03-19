<template>
  <div class="page-container">
    <md-toolbar>
      <div v-if="nomJoueurCourant !== ''" class="md-title md-toolbar-section-start">
        <AjoutScore/>
      </div>
      <div v-else>
        Pas de partie en cours : <router-link to="/new">Nouvelle Partie</router-link>
        </div>
      <div class="md-toolbar-section-end">
        <BoutonUndo/>
      <md-menu md-direction="bottom-end">
        <md-button md-menu-trigger class="md-icon-button">
          <md-icon>more_vert</md-icon>
        </md-button>

        <md-menu-content>
          <md-menu-item><router-link to="/new">Nouvelle partie</router-link></md-menu-item>
          <md-menu-item><router-link to="/">Partie en cours</router-link></md-menu-item>
        </md-menu-content>
      </md-menu>
      </div>
    </md-toolbar>
    <md-content>
      <router-view/>
    </md-content>
  </div>
</template>

<script>
import { mapGetters } from 'vuex'
import AjoutScore from '@/components/AjoutScore.vue'
import BoutonUndo from '@/components/BoutonUndo.vue'

export default {
  name: 'App',
  computed: mapGetters(['nomJoueurCourant']),
  components: {
    AjoutScore,
    BoutonUndo,
  },
}
</script>

<style lang="scss" scoped>
.md-content {
  justify-content: center;
  align-items: center;
}
</style>