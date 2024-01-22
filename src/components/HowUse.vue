<template>
  <div class="box-shadow how-use">
    <div class="how-use-logo">
      <img src="../assets/logo.png" draggable="false" />
      <p>contri-graph</p>
    </div>
    <p class="intro__title">Use</p>
    <div class="code-demo">
      <p class="title">1.安装 Install</p>
      <pre>
      <code class="language-bash">npm install contri-graph</code>
    </pre>
    </div>
    <div class="code-demo">
      <p class="title">2.使用ContriGraph</p>
      <pre>
      <code class="language-javascript">import ContriGraph from 'contrib-graph'; // 创建一个 Canvas 元素

const canvas = document.getElementById('myCanvas'); // 创建 ContriGraph 实例
const contribGraph = new ContriGraph({
  canvas: canvas,
  size: 10,
  gapSize: 5,
  data: { /* 数据 */ },
  year: 2022,
  colorParse: /* 自定义颜色解析函数 */,
}); // 渲染月份或整年的贡献图
contribGraph.render(1); // 渲染一月份 // 或 contribGraph.render(); // 渲染整年</code>
    </pre>
    </div>
    <div class="code-demo">
      <p class="title">3.data 格式</p>
      <pre>
      <code class="language-javascript">{ "2023-01-05":1, "2023-03-01":10,...any }</code>
    </pre>
    </div>
    <div class="code-demo">
      <p class="title">4.构造函数 Constructor</p>
      <pre>
      <code class="language-typescript">new ContriGraph({
  canvas: HTMLCanvasElement, // Canvas 元素
  size?: number, // 方块大小，默认为 10
  gapSize?: number, // 方块间隙大小，默认为 5
  data?: {[string]:number}, // 贡献数据，默认为空对象
  year?: number, // 年份，默认为当前年份
  colorParse?: (value: number) => string, // 颜色解析函数，默认为内置的颜色解析函数
});</code>
    </pre>
    </div>
    <div class="code-demo">
      <p class="title">5.方法 Method</p>
      <pre>
      <code class="language-typescript">// 渲染贡献图，可选择渲染指定月份（1 到 12）或整年。
render(month?: number):void</code>
    </pre>
    </div>
    <div class="code-demo">
      <p class="title">6.属性 Attribute</p>
      <pre>
      <code class="language-typescript">// 渲染贡献图，可选择渲染指定月份（1 到 12）或整年。
width:number // 生成canvas的宽
height:number //生成canvas的高</code>
    </pre>
    </div>
  </div>
</template>

<script setup>
import { onMounted } from "vue";

onMounted(() => {
  // eslint-disable-next-line no-undef
  console.log(hljs.highlightAll());
});
</script>

<style>
.title {
  font-size: 18px;
  font-weight: 600;
  margin-top: 12px;
}
.intro__title {
  font-size: 22px;
  font-weight: 800;
  border-bottom: 1px solid #ccc;
  padding: 12px 0px;
}
.how-use-logo {
  text-align: right;
  margin-top: 12px;
}
.how-use-logo img {
  width: 102px;
}
.how-use-logo p {
  font-size: 22px;
  user-select: none;
  font-weight: 800;
}
</style>
