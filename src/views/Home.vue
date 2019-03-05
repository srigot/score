<template>
  <div class="home">
    <GrilleScore/>
  </div>
</template>

<script>
// @ is an alias to /src
import GrilleScore from '@/components/GrilleScore.vue'

export default {
  name: 'home',
  components: {
    GrilleScore
  }
}
</script>
