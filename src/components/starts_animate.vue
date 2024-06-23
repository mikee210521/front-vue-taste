<template>
  <div class="starry-background">
    <div class="stars"></div>
    <div class="stars2"></div>
    <div class="stars3"></div>
  </div>
</template>

<script>
export default {
  name: 'StarryBackground'
};
</script>

<style scoped>
.starry-background {
  position: absolute;
  width: 100%;
  height: 100%;
  overflow: hidden;
  background: black;
}

.stars, .stars2, .stars3 {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: transparent;
  pointer-events: none;
}

.stars:before, .stars2:before, .stars3:before {
  content: "";
  position: absolute;
  top: 0;
  left: 0;
  width: 200%;
  height: 200%;
  background: transparent;
  box-shadow: white 0px 0px 1px 1px;
  animation: moveStars 50s linear infinite;
}

.stars {
  background: transparent;
}

.stars2 {
  opacity: 0.5;
}

.stars3 {
  opacity: 0.3;
}

@keyframes moveStars {
  from {
    transform: translateX(0) translateY(0);
  }
  to {
    transform: translateX(-100%) translateY(-100%);
  }
}
</style>