<template>
  <div class="weather">
    <div class="sunny">
      <span class="sun"></span>
    </div>
    <div class="cloudy">
      <span class="cloud"></span>
      <span class="cloud"></span>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Weather'
}
</script>

<style scoped lang="scss">
.weather {
  background: #000;
  display: flex;
  justify-content: space-around;
  flex-flow: row wrap;
  align-items: center;
  color: #fff;
  font-size: calc(1em);
}
.sunny {
  position: relative;
  font-size: calc(11em);
  width: 1em;
  height: 1em;
  margin: 0.3em;
  border-radius: 100%;
  background: linear-gradient(to top right, #fc5830 0%, #f98c24 65%);
  box-shadow: 0 0 0 0.05em currentColor inset, 0 0 0.3em -0.03em currentColor;
  .sun {
    position: absolute;
    top: 20%;
    left: 80%;
    transform: translate(-50%, -50%);
    width: 40%;
    height: 40%;
    border-radius: 100%;
    background: #ffeb3b;
    box-shadow: 0 0 0 0.02em currentColor inset, 0 0 0.3em -0.03em #fd6f21;
    // transform-origin: .1em .1em;
  }
  .sun::after {
    content: '';
    position: absolute;
    top: 0.1em;
    left: 0;
    transform: translate(-50%, -50%);
    width: 0.1em;
    height: 0.1em;
    border-radius: 100%;
    background: rgba(255, 255, 255, 0.3);
    box-shadow: -0.1em -0.1em 0 0.2em rgba(255, 255, 255, 0.1);
    animation: flare 6000ms infinite alternate linear;
  }
  @keyframes flare {
    to {
      transform: translate(-0.3em, 0.3em);
      opacity: 0.4;
      font-size: 0.2em;
    }
  }
}
.cloudy {
  position: relative;
  font-size: calc(11em);
  width: 1em;
  height: 1em;
  margin: 0.3em;
  border-radius: 100%;
  background: linear-gradient(to top right, #1b9ce2 0, #fff 90%);
  box-shadow: 0 0 0 0.05em currentColor inset, 0 0 0.3em -0.03em currentColor;
  .cloud {
    position: absolute;
    top: 0.1em;
    left: 65%;
    width: 0.37em;
    height: 0.13em;
    border-radius: 0.1em;
    background-color: #fff;
    animation: move 4000ms infinite ease-in-out;
  }
  .cloud + .cloud {
    top: 25%;
    left: 40%;
    animation: move 3700ms infinite linear;
  }
  .cloud::before {
    left: 0.05em;
    width: 0.2em;
    height: 0.2em;
  }
  .cloud::after {
    left: 0.15em;
    width: 0.15em;
    height: 0.15em;
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
      transform: translateX(-0.05em);
    }
  }
}
</style>