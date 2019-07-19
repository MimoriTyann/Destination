<template>
  <div class="weather-wrap">
    <div class="cloudy">
      <span class="cloud"></span>
      <span class="cloud"></span>
    </div>
  </div>
</template>

<script>
export default {
  name: 'weather'
}
</script>

<style scoped lang="scss">
.weather-wrap {
  background: #000;
  display: flex;
  justify-content: space-around;
  flex-flow: row wrap;
  align-items: center;
  height: 500px;
  color: #fff;
}
.cloudy {
  position: relative;
  width: 300px;
  height: 300px;
  border-radius: 100%;
  background: linear-gradient(to top right, #1b9ce2 0, #fff 90%);
  box-shadow: 0 0 0 10px currentColor inset, 0 0 100px -10px currentColor;
  .cloud {
    position: absolute;
    top: 25%;
    left: 40%;
    width: 100px;
    height: 30px;
    border-radius: 20px;
    background-color: #fff;
    animation: move 4000ms infinite ease-in-out;
  }
  .cloud + .cloud {
    top: 14%;
    left: 64%;
    animation: move 3700ms infinite linear;
  }
  .cloud::before {
    left: 15px;
    height: 50px;
    width: 50px;
  }
  .cloud::after {
    left: 45px;
    height: 35px;
    width: 35px;
  }
  .cloud::before,
  .cloud::after {
    content: '';
    position: inherit;
    border-radius: 100%;
    background-color: inherit;
    bottom: 40%;
  }
  @keyframes move {
    50% {
      transform: translateX(-10px);
    }
  }
}
</style>