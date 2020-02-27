<template lang="pug">
  #app
    DisplayUserData
</template>

<script>
import DisplayUserData from '@/components/DisplayUserData'

export default {
  name: 'App',
  components: {
    DisplayUserData
  }
}
</script>

<style lang="scss">
  @import '@/styles/main.scss';
  @import 'bulma';
</style>
