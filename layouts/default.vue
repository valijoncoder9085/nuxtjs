<template>
  <v-app dark>
    <Sidebar/>
  </v-app>
</template>

<script>
export default {
  name: 'DefaultLayout',
  data() {
    return {}
  }
}
</script>
<style lang="scss">
.page-enter-active, .page-leave-active {
  transition: all 0.5s;
}

.page-enter, .page-leave-active {
  opacity: 0;
}
</style>
