<template>
  <div class="wrap" ref="wrap" @scroll="wrapScroll">
    <div :style="topBlankStyle"></div>
    <div
      class="item"
      v-for="item in activeList"
      :key="item"
      :ref="`item-${item}`"
      :style="{height:`${(item+1)*50}px`}"
    >{{item}}</div>
    <div :style="bottomBlankStyle"></div>
  </div>
</template>

<script>
export default {
  name: 'InfiniteScroll',
  data() {
    return {
      itemList: [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10],
      activeList: [],
      topBlankHeight: 0,
      bottomBlankHeight: 0,
      activeItem: 0
    }
  },
  computed: {
    topBlankStyle() {
      return {
        height: `${this.topBlankHeight}px`
      }
    },
    bottomBlankStyle() {
      return {
        height: `${this.bottomBlankHeight}px`
      }
    }
  },
  methods: {
    wrapScroll(e) {
      //内部滚动距离
      // console.log(this.$el.scrollTop)
      //元素距顶部距离
      // console.log(this.$refs.test.offsetTop)
      //元素高度
      // console.log(this.$refs['item-2'][0].offsetHeight)

      let scrollTop = this.$el.scrollTop
      let preItemTop = this.$refs[`item-${this.activeItem}`][0].offsetTop
      let itemTop = this.$refs[`item-${this.activeItem + 1}`][0].offsetTop
      if (scrollTop > itemTop) {
        this.topBlankHeight += this.activeItem
          ? this.$refs[`item-${this.activeItem - 1}`][0].offsetHeight
          : 0
        this.activeItem += 1
        this.activeList = this.itemList.slice(
          this.activeItem - 1,
          this.activeItem + 3
        )
      } else if (scrollTop < preItemTop) {
        this.topBlankHeight -= this.activeItem
          ? this.$refs[`item-${this.activeItem + 1}`][0].offsetHeight
          : 0
        this.activeItem -= 1
        this.activeList = this.itemList.slice(
          this.activeItem - 1,
          this.activeItem + 3
        )
      }
      console.log(scrollTop + 'scrollTop')
      console.log(itemTop + 'itemTop')
    }
  },
  mounted() {
    this.activeList = this.itemList.slice(this.activeItem, this.activeItem + 4)
  }
}
</script>

<style scoped lang="scss">
.wrap {
  height: 300px;
  border: 1px solid #000;
  overflow: scroll;
  position: relative;
}
.item {
  // height: 100px;
  border: 1px solid #666;
}
</style>
