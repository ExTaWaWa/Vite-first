<template>
  <button @click="changeView(1)">顯示單向綁定</button>
  <button @click="changeView(2)">顯示雙向綁定</button>
  <button @click="changeView(100)">沒畫面</button>
<!-- v-if 直接渲染或不渲染 dom 所以 div 不顯示的就不會顯示出來 -->
  <div class="container_1" v-if="view === 1">
    <!-- 資料綁定（單向綁定） -->
    <p>資料綁定（單向綁定）</p>
    <div>{{ title }}</div>
  </div>

  <div class="container_2" v-else-if="view === 2">
    <!-- 資料綁定（雙向綁定） -->
    <p>資料綁定（雙向綁定）</p>
    <input type="text" v-model="P" />
    <p>{{ P }}</p>
  </div>

  <div v-else>
    <p>HelloWorld</p>
  </div>
  <!-- v-show 是利用 CSS 的 display 控制顯示 -->
  <div class="container_1" v-show="view === 1">
    <!-- 資料綁定（單向綁定） -->
    <p>資料綁定（單向綁定）</p>
    <div>{{ title }}</div>
  </div>

  <div class="container_2" v-show="view === 2">
    <!-- 資料綁定（雙向綁定） -->
    <p>資料綁定（雙向綁定）</p>
    <input type="text" v-model="P" />
    <p>{{ P }}</p>
  </div>

  <div v-show="view !== 1 && view !== 2">
    <p>HelloWorld</p>
  </div>
</template>

// 網頁三大元素
// 畫面 ui
// 事件 event
// 資料 data

<script setup>
import { ref } from "@vue/reactivity";

// 資料驅動畫面
const title = "TITLE";
// vue3 寫法用 ref 來監聽
const P = ref("123");
const view = ref(1);
const changeView = (n) => {
  view.value = n;
};
</script>

<style lang="scss">
.container_1 {
  border: 2px solid red;
}

.container_2 {
  border: 2px solid skyblue;
}
</style>