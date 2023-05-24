<script>
import AppHeader from './components/AppHeader.vue';
import AppMain from './components/AppMain.vue';

import { store } from './data/store';
import axios from 'axios';

export default {
  components: {
    AppHeader,
    AppMain,
  },
  data() {
    return {
      store,
    }
  },
  mounted() {
    axios.get(this.store.urlAPI).then(cards => {
      this.store.cards = cards.data.data
    })

    axios.get(this.store.urlArchetype).then(archetypes => {
      this.store.archetypes = archetypes.data
    })
  }
}
</script>

<template>
  <AppHeader />

  <AppMain />
</template>

<style lang="scss">
@use './style.scss' as *;
</style>
