<template>
  <div class="box-shadow logo-box">
    <p class="logo">contri-graph</p>
    <div class="info-flex">
      <a
        href="https://www.npmjs.com/package/contri-graph?activeTab=readme"
        class="package-shield"
        rel="noreferrer noopener"
        ><img
          data-v-5813dbef=""
          src="https://img.shields.io/npm/v/contri-graph"
          alt="https://www.npmjs.com/package/contri-graph"
      /></a>
      <a
        style="margin-left: 10px"
        data-v-5813dbef=""
        href="https://www.npmjs.com/package/contri-graph"
        class="package-shield"
        rel="noreferrer noopener"
        ><img
          data-v-5813dbef=""
          src="https://img.shields.io/npm/dw/contri-graph"
          alt="https://www.npmjs.com/package/contri-graph"
      /></a>
    </div>
    <ul>
      <li
        class="info-item"
        v-for="(item, index) in renderOfInfoList"
        :key="index"
      >
        <component :is="item.logo"></component>
        <a :href="item.address">
          {{ item.address }}
        </a>
      </li>
    </ul>
    <div class="box-banner">
      <svg height="62" width="62" viewBox="0 0 700 700" aria-hidden="true">
        <polygon
          fill="rgba(186, 38, 26, .4)"
          points="0,700 700,700 700,0 0,0"
        ></polygon>
        <polygon
          fill="#ffffff"
          points="150,550 350,550 350,250 450,250 450,550 550,550 550,150 150,150 "
        ></polygon>
      </svg>
    </div>
  </div>
</template>

<script setup>
import { Github, Package } from "lucide-vue-next";

const renderOfInfoList = [
  {
    address: "https://github.com/cairongquan/contriGraph",
    logo: Github,
  },
  {
    address: "https://www.npmjs.com/package/contri-graph",
    logo: Package,
  },
];
</script>

<style>
.logo-box {
  width: calc(50% - 10px);
  position: relative;
}
.logo {
  user-select: none;
  font-size: 22px;
  font-weight: 800;
}
.info-flex {
  margin-top: 12px;
  display: flex;
  align-items: center;
}
.info-item {
  display: flex;
  align-items: center;
  margin-top: 12px;
}
.info-item a {
  text-decoration: none;
  color: #333;
  font-size: 18px;
  margin-left: 4px;
}
.info-item a:hover {
  color: #456b43;
}
.box-banner {
  position: absolute;
  right: 12px;
  top: 12px;
}
</style>
