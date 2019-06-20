<template>
  <section>
    <div class="header-wrap">
      <div class="header-wrap-in">
        <div class="menu-btn" @click="openMenu">
          <svg class="icon menu-btn-icon">
            <use xlink:href="#icon-icon-test"></use>
          </svg>
        </div>
        <div class="logo">Destination</div>
      </div>
    </div>

    <transition name="fade">
      <div v-show="menuActive" class="menu-wrap">
        <div class="menu-cont">
          <div v-for="(title, key) in menuList" :key="key" class="title">
            <nuxt-link :to="{name: key}" class="title-first" @click.native="closeMenu">{{key}}</nuxt-link>
            <nuxt-link
              v-for="(item, index) in title"
              :key="index"
              :to="{name: `${key}-${item}`}"
              class="title-second"
              @click.native="closeMenu"
            >{{item}}</nuxt-link>
          </div>
        </div>
      </div>
    </transition>

    <div v-show="menuActive" class="menu-mask" @click="closeMenu"></div>
  </section>
</template>

<script>
export default {
  name: 'Header',
  data() {
    return {
      menuActive: false,
      menuList: {
        index: [],
        point: ['point1', 'point2', 'point3'],
        music: []
      }
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
// header
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
    z-index: 50;
    .menu-btn {
      position: absolute;
      top: 0;
      left: 0;
      height: 50px;
      width: 50px;
      display: flex;
      justify-content: center;
      align-items: center;
      color: #fff;
      font-size: 25px;
      font-weight: bold;
      background: #a8da70;
      border-bottom-right-radius: 100%;
      .menu-btn-icon {
        transform: translate(-5px, -5px);
      }
    }
    .logo {
      font-size: 20px;
      font-weight: bold;
      color: #000;
    }
  }
}

// menu
.menu-wrap {
  position: fixed;
  width: 80%;
  left: 0;
  top: 0;
  bottom: 0;
  background: #fff;
  z-index: 101;
  .menu-cont {
    padding: 20px;
    .title {
      a {
        display: block;
        &.nuxt-link-exact-active {
          color: aqua;
        }
      }
    }
  }
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

// animate
.fade-enter-active,
.fade-leave-active {
  transition: all 0.2s linear;
}
.fade-enter,
.fade-leave-to {
  transform: translate3d(-100%, 0, 0);
}
</style>
