<script>

import AppHeader from './components/AppHeader.vue';

import AppMain from './components/AppMain.vue';

export default {
  data() {
    return {
      loading: true
    }
  },
  components: {
    AppHeader,
    AppMain
  }
}
  
</script>

<template>

  <AppHeader />
  
  <AppMain />
  
</template>

<style lang="scss">
 @use './style/general.scss' as *;
</style>
