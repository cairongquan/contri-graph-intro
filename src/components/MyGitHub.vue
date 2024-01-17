<template>
  <div class="box-shadow my-github-box">
    <div class="git-info">
      <img
        alt=""
        src="https://avatars.githubusercontent.com/u/38879616?v=4"
        width="60"
        height="60"
        class="avatar"
      />
      <div style="margin-left: 10px">
        <a href="https://github.com/cairongquan">
          <img
            src="https://img.shields.io/github/stars/cairongquan"
            alt="https://img.shields.io/github/stars/cairongquan"
          />
        </a>
        <p>
          <a href="https://twitter.com/GuoRanYa233">
            <img src="https://img.shields.io/twitter/follow/GuoRanYa233" />
          </a>
        </p>
      </div>
    </div>
    <canvas style="margin: 10px auto" id="my-canvas"></canvas>
  </div>
</template>

<script setup>
import contriGraph from "contri-graph";
import axios from "axios";

import { onMounted, ref } from "vue";

const contriGraphRef = ref(null);

function switchColorHandle(num) {
  num = Number(num);
  if (num === 0) return "#ebedf0";
  if (num < 2) return "#ace7ae";
  if (num > 2 && num < 5) return "#69c16e";
  if (num > 5 && num < 9) return "#539f57";
  else return "#386c3e";
}

onMounted(() => {
  const dataObj = {};
  axios("./myGit2024.json").then(({ data: response }) => {
    response.contributions.forEach((item) => {
      dataObj[item.date] = item.intensity;
    });
    contriGraphRef.value = new contriGraph({
      canvas: document.querySelector("#my-canvas"),
      data: dataObj,
      size: 8,
      gapSize: 2.4,
      year: 2023,
      colorParse: switchColorHandle,
    });
    contriGraphRef.value.render();
  });
});
</script>

<style>
.my-github-box {
  width: calc(50% - 10px);
}
.avatar {
  border-radius: 50%;
}
.git-info {
  display: flex;
  align-items: center;
}
</style>
