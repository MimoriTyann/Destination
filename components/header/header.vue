<template>
  <section>
    <div class="header-wrap">
      <div class="header-wrap-in">
        <div class="menu-btn" @click="openMenu()">M</div>
        <div class="logo">Destination</div>
      </div>
    </div>

    <transition name="fade">
      <div v-show="menuActive" class="menu-wrap">
        <div class="title">Test</div>
      </div>
    </transition>

    <div v-show="menuActive" class="menu-mask" @click="closeMenu()"></div>
  </section>
</template>

<script>
export default {
  name: 'Header',
  data() {
    return {
      menuActive: false
    }
  },
  methods: {
    openMenu() {
      document.body.classList.add('flow-hidden')
      this.menuActive = true
    },
    closeMenu() {
      document.body.classList.remove('flow-hidden')
      this.menuActive = false
    }
  }
}
</script>

<style scoped lang="scss">
.header-wrap {
  position: relative;
  height: 50px;
  .header-wrap-in {
    position: fixed;
    top: 0;
    display: flex;
    justify-content: center;
    align-items: center;
    height: 50px;
    width: 100%;
    background: #8eff8e;
    z-index: 50;
    .menu-btn {
      position: absolute;
      top: 0;
      left: 0;
      height: 30px;
      line-height: 30px;
      font-size: 20px;
      font-weight: bold;
      padding: 10px;
    }
    .logo {
      font-size: 20px;
      font-weight: bold;
      color: #000;
    }
  }
}

.menu-wrap {
  position: fixed;
  width: 80%;
  left: 0;
  top: 0;
  bottom: 0;
  background: #fff;
  padding: 20px 0;
  z-index: 101;
}

.menu-mask {
  position: fixed;
  top: 0;
  bottom: 0;
  width: 100%;
  height: 100%;
  z-index: 100;
  background: rgba(7, 7, 7, 0.5);
}

.fade-enter-active,
.fade-leave-active {
  transition: all 0.2s linear;
}
.fade-enter,
.fade-leave-to {
  transform: translate3d(-100%, 0, 0);
}
</style>
