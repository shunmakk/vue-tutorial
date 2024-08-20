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
//条件分岐
const error = "エラー発生";
const errorBoolean = true;
const errorNothing = "";
const stock = 0;
const errorVshow = true;
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
  <!-- 条件分岐 -->
  <div v-if="error">{{ error }}</div>
  <div v-if="errorBoolean">エラーtrue</div>
  <div v-if="errorNothing">{{ errorNothing }}</div>
  <div v-else>エラーはないですよ~</div>

  <div v-if="stock > 5">まだ商品に在庫数に余裕があります</div>
  <div v-else-if="stock === 0">申し訳ございません。現在在庫切れです</div>
  <div v-else>在庫数が少なくなっています。お急ぎください</div>

  <div v-if="errorVshow">
    エラー（v-showの方がv-ifよりもパフォーマンス的に上）
  </div>
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
