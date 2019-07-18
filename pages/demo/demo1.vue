<template>
  <section>
    <div class="demo-title"></div>
    <infiniteScroll></infiniteScroll>
  </section>
</template>

<script>
import infiniteScroll from '~/components/demo/infinite-scroll'
export default {
  components: {
    infiniteScroll
  }
}
</script>

<style scoped lang="scss">
.demo-title {
  height: 200px;
}
</style>