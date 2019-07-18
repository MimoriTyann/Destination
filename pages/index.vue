<template>
  <section>
    <div class="index-content">index</div>
    <nuxt-link :to="{name: 'demo-demo1'}">demo1</nuxt-link>
    <nuxt-link :to="{name: 'point'}">Change</nuxt-link>
  </section>
</template>

<script>
export default {}
</script>

<style scoped lang="scss">
.index-content {
  height: 100px;
}
</style>