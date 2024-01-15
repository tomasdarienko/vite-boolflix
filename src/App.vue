<script >
import AppHeader from './components/AppHeader.vue';
import AppMain from './components/AppMain.vue';
import { store } from './store';

export default {

  components: {
    AppHeader,
    AppMain
    
  },

  data() {
    return {
      store
    }
  },
}
</script>

<template>
<body>
  <AppHeader />
  <AppMain />
</body>

</template>

<style lang="scss" scoped>
@use '../styles/general.scss' as*;
</style>
