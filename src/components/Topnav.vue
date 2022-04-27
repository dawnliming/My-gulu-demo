<template>
  <div class="topNav">
    <div class="logo" @click="toggleMenu">LOGO</div>
    <ul class="menu">
      <li>菜单1</li>
      <li>菜单2</li>
      <span class="toggleAside"></span>
    </ul>
  </div>
</template>

<script lang="ts">

import {inject, Ref} from "vue";

export default {
  name: 'Topnav',
  setup(){
    const menuVisible = inject<Ref<boolean>>('menuVisible')
    const toggleMenu = ()=>{
      menuVisible.value = !menuVisible.value
    }
    return {toggleMenu}
  }
}
</script>

<style lang="scss" scoped >
.topNav{
  padding: 16px;
  display: flex;
  background: pink;
  position: relative;
  z-index: 10;
  justify-content: center;
  align-items: center;
  > .logo{
    max-width: 6em;
    margin-right: auto;
  }
  > .menu{
    display: flex;
    white-space: nowrap;
    flex-wrap: nowrap;
    > li{
      margin: 0 1em;
    }
  }
  @media (max-width: 500px) {
    > .menu{display: none}
    > .logo{margin: 0 auto}
  }
}
</style>