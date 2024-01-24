<script setup>
import { onMounted, reactive, ref, watch } from "vue";
import axios from "axios";

import ContriGraph from "contri-graph";

onMounted(() => getDateTemplateData());

const renderOption = reactive({
  size: 10,
  gapSize: 5,
  canvas: null,
  year: 2024,
  // data: {},
  colorParse: (num) => {
    num = Number(num);
    if (num === 0) return "#ebedf0";
    if (num < 2) return "#ace7ae";
    if (num > 2 && num < 5) return "#69c16e";
    if (num > 5 && num < 9) return "#539f57";
    else return "#386c3e";
  },
});

const getDateTemplateData = async () => {
  const { data: response } = await axios({
    method: "get",
    url: "./dateData.json",
  });
  console.log(response);
  renderOption.data = response;
  renderCalendar();
};

const canShowCode = ref(false);
watch(canShowCode, (val) => {
  // eslint-disable-next-line no-undef
  val && hljs.highlightAll();
});

const renderCanvasTopHeigh = ref(0);
const renderCalendar = () => {
  const topCanvasRef = new ContriGraph({
    canvas: document.querySelector("#demo-canvas"),
    colorParse: renderOption.colorParse,
    size: 13,
    gapSize: 8,
    data: renderOption.data,
    year: 2024,
  });
  topCanvasRef.render();
  renderCanvasTopHeigh.value = topCanvasRef.height;

  const introList = document.querySelector(".intro__list");
  new Array(12).fill(null).forEach((item, index) => {
    const canvas = document.createElement("canvas");
    const li = document.createElement("li");
    const p = Object.assign(document.createElement("p"), {
      innerHTML: index + 1 + "月",
    });
    li.className = "li-dom";
    li.appendChild(canvas);
    li.appendChild(p);
    renderOption.canvas = canvas;
    new ContriGraph(renderOption).render(index + 1);
    introList.appendChild(li);
  });
};
</script>

<template>
  <div class="box-shadow demo-box">
    <p class="intro__title">
      <span>Demo: 2024 Contributions</span>
      <span @click="canShowCode = !canShowCode">{{
        (canShowCode && "view") || "code"
      }}</span>
    </p>
    <div v-show="!canShowCode">
      <div class="demo-top" :style="{ height: renderCanvasTopHeigh + 'px' }">
        <canvas id="demo-canvas"></canvas>
      </div>
      <ul class="intro__list"></ul>
    </div>
    <div v-show="canShowCode">
      <pre>
        <code class="language-typescript">
import { onMounted, reactive, ref, watch } from "vue";
import axios from "axios";

import ContriGraph from "contri-graph";

onMounted(() => getDateTemplateData());

const renderOption = reactive({
  size: 10,
  gapSize: 5,
  canvas: null,
  year: 2024,
  // data: {},
  colorParse: (num) => {
    num = Number(num);
    if (num === 0) return "#ebedf0";
    if (num  2) return "#ace7ae";
    if (num > 2 && num  5) return "#69c16e";
    if (num > 5 && num  9) return "#539f57";
    else return "#386c3e";
  },
});

const getDateTemplateData = async () => {
  const { data: response } = await axios({
    method: "get",
    url: "./dateData.json",
  });
  renderOption.data = response;
  renderCalendar();
};

const canShowCode = ref(false);
watch(canShowCode, (val) => {
  // eslint-disable-next-line no-undef
  val && hljs.highlightAll();
});

const renderCanvasTopHeigh = ref(0);
const renderCalendar = () => {
  const topCanvasRef = new ContriGraph({
    canvas: document.querySelector("#demo-canvas"),
    colorParse: renderOption.colorParse,
    size: 13,
    gapSize: 8,
    data: renderOption.data,
    year: 2024,
  });
  topCanvasRef.render();
  renderCanvasTopHeigh.value = topCanvasRef.height;

  const introList = document.querySelector(".intro__list");
  new Array(12).fill(null).forEach((item, index) => {
    const canvas = document.createElement("canvas");
    const li = document.createElement("li");
    const p = Object.assign(document.createElement("p"), {
      innerHTML: index + 1 + "月",
    });
    li.className = "li-dom";
    li.appendChild(canvas);
    li.appendChild(p);
    renderOption.canvas = canvas;
    new ContriGraph(renderOption).render(index + 1);
    introList.appendChild(li);
  });
};
        </code>
      </pre>
    </div>
  </div>
</template>

<style>
.intro__list {
  margin-top: 12px;
}
.intro__list:nth-child(-n + 4) {
  border-top: 0px;
}
.li-dom {
  padding: 12px;
  width: calc(25% - 12px);
  display: inline-block;
  border: 1px solid #ccc;
  position: relative;
  margin-bottom: 12px;
  margin-right: 12px;
  transition: all ease 220ms;
  border-radius: 4px;
}
.li-dom:hover {
  box-shadow: 1px 1px 12px 4px rgba(0, 0, 0, 0.1);
  border-color: #fff;
}
.li-dom p {
  position: absolute;
  right: 12px;
  top: 12px;
  font-size: 18px;
  user-select: none;
  font-weight: 800;
}
.demo-top {
  margin-top: 12px;
  position: relative;
}
.demo-top canvas {
  position: absolute;
  left: 50%;
  transform: translateX(-50%);
}
.intro__title {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.intro__title :nth-child(2) {
  font-size: 16px;
  color: #fff;
  display: block;
  padding: 6px 14px;
  background-color: #7fbf77;
  border-radius: 2px;
  user-select: none;
  cursor: pointer;
  transition: box-shadow ease 220ms;
}
.intro__title :nth-child(2):hover {
  box-shadow: 1px 1px 12px 2px rgba(0, 0, 0, 0.1);
}
</style>
