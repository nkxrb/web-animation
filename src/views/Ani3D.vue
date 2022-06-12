<template>
  <div class="d3 block">
    <h4>3D动画</h4>
    <div class="d3-parent">
      <div class='d3-center' 
        :style="`animation:${turnControl.animation} 10s infinite linear; animation-play-state:${turnControl.play};`"
      >
        <div 
          class='d3-child' 
          v-for="(item, index) in turns" 
          :key="{index}" 
          :style="`transform:rotateY(${360/turns.length*index}deg) rotateX(80deg) translateZ(100px)`"
        >
          {{item.name}}
        </div>
        <div 
          class='d3-child' 
          v-for="(item, index) in turns" 
          :key="{index}" 
          :style="`transform:rotateY(${360/turns.length*index}deg) rotateX(40deg) translateZ(100px)`"
        >
          {{item.name}}
        </div>
        <div 
          class='d3-child' 
          v-for="(item, index) in turns" 
          :key="{index}" 
          :style="`transform:rotateY(${360/turns.length*index}deg) rotateX(0deg) translateZ(80px)`"
        >
          {{item.name}}
        </div>
        <div 
          class='d3-child' 
          v-for="(item, index) in turns" 
          :key="{index}" 
          :style="`transform:rotateY(${360/turns.length*index}deg) rotateX(-40deg) translateZ(100px)`"
        >
          {{item.name}}
        </div>
        <div 
          class='d3-child' 
          v-for="(item, index) in turns" 
          :key="{index}" 
          :style="`transform:rotateY(${360/turns.length*index}deg) rotateX(-80deg) translateZ(100px)`"
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
  animation: "autoRotateY"
})

const play = ()=>{
  turnControl.play = turnControl.play==='paused' ? 'running' : 'paused'
}

const changeAnimation = (name) =>{
  turnControl.animation = name
}

</script>