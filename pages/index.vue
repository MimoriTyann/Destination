<template>
  <section>
    <header-model></header-model>

    <nuxt-child></nuxt-child>
  </section>
</template>

<script>
import HeaderModel from '~/components/header/header.vue'

export default {
  components: {
    HeaderModel
  }
}
</script>

<style scoped lang="scss">
</style>
