<template>
  <div ref="dragWrap" class="drag-wrap">
    <div
      class="box"
      :style="{left: `${positionX}px`, top: `${positionY}px`}"
      @touchstart="dragStart"
      @touchmove="dragMove"
    ></div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      startX: 0,
      startY: 0,
      positionX: 0,
      positionY: 0,
      touchX: 0,
      touchY: 0,
      dragX: 0,
      dragY: 0
    }
  },
  methods: {
    dragStart(e) {
      // 获取元素初始位置
      this.startX = e.target.offsetLeft
      this.startY = e.target.offsetTop
      // 获取点击初始位置
      this.touchX = e.touches[0].clientX
      this.touchY = e.touches[0].clientY
    },
    dragMove(e) {
      // 计算偏移量
      this.dragX = e.touches[0].clientX - this.touchX
      this.dragY = e.touches[0].clientY - this.touchY
      // 计算元素拖动位置
      const moveToX = this.startX + this.dragX
      const moveToY = this.startY + this.dragY
      if (
        moveToX > 0 &&
        moveToX < this.$refs.dragWrap.offsetWidth - e.target.offsetWidth
      ) {
        this.positionX = moveToX
      }
      if (
        moveToY > 0 &&
        moveToY < this.$refs.dragWrap.offsetHeight - e.target.offsetHeight
      ) {
        this.positionY = moveToY
      }
    }
  }
}
</script>

<style scoped lang="scss">
.drag-wrap {
  position: absolute;
  overflow: hidden;
  width: 100%;
  height: 500px;
  background: rgb(247, 241, 167);
  .box {
    position: absolute;
    width: 50px;
    height: 50px;
    background: rgb(255, 208, 208);
  }
}
</style>