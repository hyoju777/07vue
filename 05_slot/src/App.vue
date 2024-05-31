<template>
    <div id="app">
      <div class="image-container">
        <img v-bind:class="animationClass" src="@/assets/hong-gildong.jpg" alt="Hong Gildong" />
      </div>
      <div class="buttons">
        <button @click="startAnimation('left')">Left</button>
        <button @click="startAnimation('right')">Right</button>
        <button @click="startAnimation('bottom')">Bottom</button>
        <button @click="startAnimation('top')">Top</button>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        animationClass: ''
      };
    },
    methods: {
      startAnimation(direction) {
        this.animationClass = `fade-${direction}`;
        setTimeout(() => {
          this.animationClass = '';
        }, 2000); // 애니메이션 지속 시간과 일치시킵니다.
      }
    }
  };
  </script>
  
  <style scoped>
  .image-container {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 300px;
    position: relative;
    overflow: hidden;
  }
  
  img {
    width: 100px;
    height: 100px;
    position: absolute;
    transition: transform 2s, opacity 2s;
    opacity: 0;
  }
  
  /* 애니메이션 클래스 */
  .fade-left {
    transform: translateX(-100%);
    opacity: 1;
  }
  
  .fade-right {
    transform: translateX(100%);
    opacity: 1;
  }
  
  .fade-bottom {
    transform: translateY(100%);
    opacity: 1;
  }
  
  .fade-top {
    transform: translateY(-100%);
    opacity: 1;
  }
  
  /* 초기 위치를 설정합니다 */
  img:not(.fade-left):not(.fade-right):not(.fade-bottom):not(.fade-top) {
    transform: translate(0, 0);
    opacity: 1;
  }
  
  .buttons {
    display: flex;
    justify-content: center;
    margin-top: 20px;
  }
  
  button {
    margin: 0 10px;
    padding: 10px 20px;
    cursor: pointer;
  }
  </style>