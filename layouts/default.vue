<template>
  <div>
    <header-model></header-model>
    
    <nuxt/>
  </div>
</template>

<script>
import HeaderModel from '~/components/header/header'

export default {
  components: {
    HeaderModel
  }
}
</script>

<style lang="scss">
.icon {
  width: 1em;
  height: 1em;
  vertical-align: -0.15em;
  fill: currentColor;
  overflow: hidden;
}
</style>
