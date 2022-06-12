<template>
  <div class="wrapper">
    <div class="base block">
      <h4>基础动画</h4>
      <template v-for="prop in baseList" :key="prop">
        <div class="item" >
          <div :class="`${prop}-hover`"></div>
          <p>{{prop}}</p>
        </div>
      </template>
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