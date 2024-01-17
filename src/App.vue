<template>
  <div class="app">
    <div class="app-header">
      <my-git-hub></my-git-hub>
      <logo-view></logo-view>
    </div>
    <div style="margin-top: 20px">
      <how-use></how-use>
    </div>
  </div>
</template>

<script setup>
import LogoView from "./components/LogoView.vue";
import MyGitHub from "./components/MyGitHub.vue";
import HowUse from "./components/HowUse.vue";
</script>

<style>
#app {
  width: 1200px;
  margin: 0 auto;
  padding: 20px;
}
.app-header {
  display: flex;
  justify-content: space-between;
}
</style>
