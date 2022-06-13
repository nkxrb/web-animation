<template>
  <div class="advanced block">
    <div style="width: 100%;">
      <h4>进阶动画</h4>
      <p>实现小球绕椭圆运行</p>
    </div>
    <div class="canvas">
      <div class="turntable"></div>

      <div class="move-x">
        <div class="ball move-y"></div>
      </div>
      <!-- <div class="move-x2">
        <div class="ball move-y2"></div>
      </div>
      <div class="move-x3">
        <div class="ball move-y3"></div>
      </div> -->
      
    </div>
  </div>
</template>

<script setup lang="ts">

</script>

<style lang="scss">

.canvas{
  width: 200px;
  height: 200px;
  background-color: #684941b8;
  position: relative;
}
.canvas+.canvas{
  margin-left: 12px;
}

.turntable{
  position: absolute;
  top: 35%;
  left: 16px;
  background-image: url('../assets/egg-tai.png');
  background-size: 100% 100%;
  width: 175px;
  height: 175px;
}

.ball{
  width: 31px;
  height: 40px;
  background-image: url('../assets/egg.png');
  background-size: 100% 100%;
  position: absolute;
  top: 34%;
  left: 30px;
  z-index: 3;
}

.move-x{
  position: absolute;
  top: 25%;
  animation: moveX 5s cubic-bezier(0.5, 0, 0.5, 1) -2.5s infinite alternate;
  .move-y{
    animation: moveY 5s cubic-bezier(0.5, 0, 0.5, 1) infinite alternate;
  }
}

.move-x2{
  position: absolute;
  top: 25%;
  animation: moveX 5s cubic-bezier(0.5, 0, 0.5, 1) -5s infinite alternate;
  .move-y2{
    animation: moveY 5s cubic-bezier(0.5, 0, 0.5, 1) -2.5s infinite alternate;
  }
}


.move-x3{
  position: absolute;
  top: 25%;
  animation: moveX 5s cubic-bezier(0.5, 0, 0.5, 1) -2.5s infinite alternate;
  .move-y3{
    animation: moveY 5s cubic-bezier(0.5, 0, 0.5, 1) infinite alternate;
  }
}


.move-x-z{
  animation: rotateZ 10s infinite linear;
}

@keyframes moveX {
  0% {
    transform: translateX(0px);
  }
  100% {
    transform: translateX(110px);
  }
}

@keyframes moveY {
  0% {
    transform: translateY(20px) scale(1);
  }
  100% {
    transform: translateY(-10px) scale(0.8);
  }
}

@keyframes translateYdaly30 {
  0% {
    transform: translateY(0px);
  }
  100% {
    transform: translateY(calc(200px - 100%));
  }
}

@keyframes rotateZ {
  0% {
    transform: rotateZ(0);
  }
  100% {
    transform: rotateZ(-360deg);
  }
}

</style>