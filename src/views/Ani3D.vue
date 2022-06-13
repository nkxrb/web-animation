<template>
  <div class="d3 block">
    <h4>3D动画</h4>
    <div class="d3-parent" @click="changeZ">
      <div class='d3-center' 
        :style="`animation:${turnControl.animation} 10s infinite linear; animation-play-state:${turnControl.play};`"
      >
        <div 
          class='d3-child' 
          v-for="(item, index) in turns" 
          :key="index" 
          :style="`transform:rotateY(${360/turns.length*index}deg) rotateX(80deg) translateZ(${turnControl.transZ}px)`"
        >
          {{item.name}}
        </div>
        <div 
          class='d3-child' 
          v-for="(item, index) in turns" 
          :key="index" 
          :style="`transform:rotateY(${360/turns.length*index}deg) rotateX(40deg) translateZ(${turnControl.transZ}px)`"
        >
          {{item.name}}
        </div>
        <div 
          class='d3-child' 
          v-for="(item, index) in turns" 
          :key="index" 
          :style="`transform:rotateY(${360/turns.length*index}deg) rotateX(0deg) translateZ(${turnControl.transZ}px)`"
        >
          {{item.name}}
        </div>
        <div 
          class='d3-child' 
          v-for="(item, index) in turns" 
          :key="index" 
          :style="`transform:rotateY(${360/turns.length*index}deg) rotateX(-40deg) translateZ(${turnControl.transZ}px)`"
        >
          {{item.name}}
        </div>
        <div 
          class='d3-child' 
          v-for="(item, index) in turns" 
          :key="index" 
          :style="`transform:rotateY(${360/turns.length*index}deg) rotateX(-80deg) translateZ(${turnControl.transZ}px)`"
        >
          {{item.name}}
        </div>
      </div>
    </div>

    <div class="d3-btns">
      <button @click="play">开始/暂停</button>
      <button @click="()=> changeAnimation('autoRotateX')">autoRotateX</button>
      <button @click="()=> changeAnimation('autoRotateY')">autoRotateY</button>
      <button @click="()=> changeAnimation('autoRotateXY')">autoRotateXY</button>
    </div>
  </div>
</template>

<script setup lang="ts">
import { reactive } from 'vue'
import './index.scss'
import './ani-base.scss'

const baseList = reactive([
  'rotateX','rotateY','rotateZ',
  'translateX','translateY','translateZ',
  'scale','skewX','skewY'
])

const turns = reactive([
  { name: '1' }, { name: '2' }, { name: '3' }, { name: '4' }, { name: '5' }, { name: '6' }, { name: '7' }, { name: '8' },
  { name: '1' }, { name: '2' }, { name: '3' }, { name: '4' }, { name: '5' }, { name: '6' }, { name: '7' }, { name: '8' }
])

const turnControl = reactive({
  play: "running",
  animation: "autoRotateY",
  transZ: 50,
})

const play = ()=>{
  turnControl.play = turnControl.play==='paused' ? 'running' : 'paused'
}

const changeAnimation = (name) =>{
  turnControl.animation = name
}

const changeZ = () => {
  turnControl.transZ = turnControl.transZ === 150 ? 50:150
}

</script>

<style lang="scss">

.d3-parent{
  width: 100%;
  height: 560px;
  background-color: azure;
  /* 透视距离 */
  perspective: 1800px;
  /* 透视倾斜度 */
  perspective-origin: 50% 50%;
  display: flex;
  align-items: center;
  justify-content: center;

  .d3-center{
    width: 0px;
    height: 0px;
    background-color: red;
    position: relative;
    /* 3维空间 */
    transform-style: preserve-3d;
    /* 执行动画 */
    animation: autoRotateY 5s infinite linear;
    transform-origin: center;

    .d3-child {
      width: 50px;
      height: 50px;
      /* 反面的不显示 */
      backface-visibility: hidden;
      /* 绝对位置--相对于中心点 */
      position: absolute;
      display: flex;
      align-items: center;
      justify-content: center;
      border-radius: 25px;
      transition: transform 2s ease-in-out;
      background-image: linear-gradient(to top, #eea2a2 0%, #bbc1bf 19%, #57c6e1 42%, #b49fda 79%, #7ac5d8 100%);
    }
  }
}

@keyframes autoRotateX {
  from {
    transform: rotateX(0deg);
  }
  to {
    transform: rotateX(-360deg);
  }
}

@keyframes autoRotateY {
  from {
    transform: rotateY(0deg);
  }
  to {
    transform: rotateY(-360deg);
  }
}

@keyframes autoRotateXY {
  from {
  }
  to {
    transform: rotateY(-360deg) rotateX(-360deg);
  }
}
</style>>