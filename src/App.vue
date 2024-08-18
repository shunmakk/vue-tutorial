<script setup>
console.log("Hello World!");
let message = "Hello World";
const message2 = "<h3>v-htmlディレクティブ</h3>";

//関数の実行
const upperCase = () => {
  message = message.toUpperCase();
};
upperCase();
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
</template>

<style scoped>
/* .logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
} */
</style>
