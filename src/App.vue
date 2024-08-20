<script setup>
console.log("Hello World!");
let message = "Hello World";
const message2 = "<h3>v-htmlディレクティブ</h3>";

//関数の実行
const upperCase = () => {
  message = message.toUpperCase();
};
upperCase();

//binding
const link = "https://google.com";
const isActive = true;
const isBack = true;
const styleObjcet = {
  color: "blue",
  fontWeight: 900,
};
</script>

<template>
  <h1>Vue3 入門</h1>
  <p>{{ message }}</p>
  <div>{{ message.length * 100 }}</div>
  <div>{{ message.length > 10 ? "long" : "short" }}</div>
  <!-- v-textディレクティブ -->
  <p v-text="message"></p>
  <!-- v-htmlディレクティブ -->
  <div v-html="message2"></div>
  <!-- binding -->
  <div>
    <a v-bind:href="link">Google</a>
  </div>
  <p class="underline" :class="{ active: isActive, back: isBack }">
    v-bindの設定方法の確認(全体のクラスが適用)
  </p>
  <p :class="isActive && 'active'">v-bindの設定方法の確認(論理演算子)</p>
  <p :style="styleObjcet">v-bindの設定方法の確認（style objcet）</p>
</template>

<style>
.active {
  color: red;
  font-weight: 900;
}
.underline {
  text-decoration: underline;
}
.back {
  background-color: black;
}
</style>
