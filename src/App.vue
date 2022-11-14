<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
  <div class="header">
    <div class="logo">
      <img alt="logo" src="@/assets/logo.png" />
      <RouterLink to="/">
        PokerDealer
      </RouterLink>
    </div>
    <div class="btn-group">
      <RouterLink class="btn" to="/about">关于</RouterLink>
    </div>
  </div>
  <RouterView />
</template>

<style scoped lang="scss">
.header {
  height: 40px;
  padding: 5px 10px;
  display: flex;
  justify-content: space-between;
  align-items: center;

  .btn-group {
    .btn {
      height: 30px;
      display: inline-block;
      margin-left: 10px;
      margin-top: 2px;
      line-height: 30px;
      text-align: center;
      border-radius: 5px;
      font-family: "SCM, NFR";
      font-weight: bold;
      padding: 0 20px;
      border: 1px solid #000;
      background: #fff;
      transition: all .6s;
      &:hover {
        filter: invert(1);
      }
    }
  }
}

.logo {
  height: 40px;
  line-height: 40px;
  display: flex;
  align-items: center;
  font-family: "SCM";
  font-weight: bold;
  font-size: 20px;

  img {
    height: 40px;
    margin-right: 10px;
    border-right: 2px solid #000;
  }
}

</style>
