<template>
  <section>
    <div class="index-content">index</div>
    <nuxt-link :to="{name: 'index-point'}">Change</nuxt-link>
  </section>
</template>

<script>
export default {}
</script>

<style scoped lang="scss">
.index-content {
  height: 1000px;
  background: #a9dbbc;
}
</style>