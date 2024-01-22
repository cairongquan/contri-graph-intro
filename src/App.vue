<template>
  <div class="app">
    <div class="app-header">
      <logo-view></logo-view>
      <my-git-hub></my-git-hub>
    </div>
    <div style="margin-top: 20px">
      <how-use></how-use>
    </div>
    <div style="margin-top: 20px">
      <demo-box></demo-box>
    </div>
  </div>
</template>

<script setup>
import LogoView from "./components/LogoView.vue";
import MyGitHub from "./components/MyGitHub.vue";
import HowUse from "./components/HowUse.vue";
import DemoBox from "./components/DemoBox.vue";
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
