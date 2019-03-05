<template>
  <div class="page-container">
    <md-toolbar>
      <div class="md-title md-toolbar-section-start">
        <AjoutScore/>
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
import AjoutScore from '@/components/AjoutScore.vue'
import BoutonUndo from '@/components/BoutonUndo.vue'

export default {
  name: 'App',
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