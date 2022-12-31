<template>
  <div class="main">
    <div :class="['navigation', { active: active }]" @click="onClick()">
      <span style="--i: 0; --x: -1; --y: 0">
        <img src="../assets/icons/settings.svg" />
      </span>
      <span style="--i: 1; --x: 1; --y: 0">
        <img src="../assets/icons/people.svg" />
      </span>
      <span style="--i: 2; --x: 0; --y: -1">
        <img src="../assets/icons/chatbox.svg" />
      </span>
      <span style="--i: 3; --x: 0; --y: 1">
        <img src="../assets/icons/play-circle.svg" />
      </span>
      <span style="--i: 4; --x: -1; --y: 1">
        <img src="../assets/icons/videocam.svg" />
      </span>
      <span style="--i: 5; --x: -1; --y: -1">
        <img src="../assets/icons/print.svg" />
      </span>
      <span style="--i: 6; --x: 1; --y: -1">
        <img src="../assets/icons/mail.svg" />
      </span>
      <span style="--i: 7; --x: 1; --y: 1">
        <img src="../assets/icons/image.svg" />
      </span>
    </div>

    <div class="close" @click="onClick">
      <img src="../assets/icons/close.svg" />
    </div>
  </div>
</template>

<script setup lang="ts">
import 'assets/main.scss'

const active = ref(false)

function onClick() {
  active.value = !active.value
}
</script>

<style scoped lang="scss">
.main {
  position: relative;
  display: flex;
  justify-content: center;
  align-items: center;
  width: 170px;
  height: 170px;
  cursor: pointer;
  .navigation {
    position: relative;
    display: flex;
    width: 40px;
    height: 40px;
    justify-content: center;
    align-items: center;
    transition: 0.5s;
    &.active {
      span {
        width: 45px;
        height: 45px;
        background: #1f2536;
        transform: translate(calc(60px * var(--x)), calc(60px * var(--y)));
        img {
          opacity: 1;
          font-size: 5px;
          transition: 2s;
        }
      }
      ~ .close {
        width: 40px;
        height: 40px;
        transition-delay: 1s;
        background: #2dfc52;
        img {
          width: 25px;
          scale: 1;
          transition-delay: 1s;
        }
      }
    }
    span {
      position: absolute;
      width: 7px;
      height: 7px;
      background: #fff;
      transform: translate(calc(14px * var(--x)), calc(14px * var(--y)));
      transition: transform 0.5s, width 0.5s, height 0.5s, background 0.5s;
      transition-delay: calc(0.1s * var(--i));
      display: flex;
      align-items: center;
      justify-content: center;
      :hover {
        filter: drop-shadow(0 0 2px #2dfc52) drop-shadow(0 0 5px #2dfc52)
          drop-shadow(0 0 15px #2dfc52);
      }
      img {
        transition: 0.5s;
        opacity: 0;
        width: 25px;
      }
    }
  }
  .close {
    position: absolute;
    width: 7px;
    height: 7px;
    background: #fff;
    transition: 0.5s;
    transition-delay: 0.4s;
    display: flex;
    align-items: center;
    justify-content: center;
    cursor: pointer;
    img {
      transition: 0.5s;
      scale: 0;
      width: 0px;
    }
  }
}
</style>
