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

//リストの表示1
const lan = ["Java", "JavaScript", "TypeScript", "Pyhton"];
const lanVfor = ["Java", "JavaScript", "TypeScript", "Pyhton", "PHP", "C"];
const users = [
  { id: 1, name: "John Doe", email: "john@test.com", admin: true },
  { id: 2, name: "Jane Doe", email: "jane@example.com", admin: false },
  { id: 3, name: "Kevin MacDonald", email: "kevin@test.com", admin: false },
];
const userobj = {
  id: 1,
  name: "taro",
  email: "taro@test.com",
  admin: true,
};

//クリックイベント
const clickButton = (msg) => {
  console.log(msg);
};

const clickEvent = (event) => {
  console.log(event.target);
  event.target.style.backgroundColor = "red";
};

const send = (event) => {
  event.preventDefault();
  console.log("send");
};

const send2 = () => {
  console.log("send2");
};

//Reactivity
import { ref } from "vue";
const count = ref(0);
console.log(count.value);

import { reactive } from "vue";
const state = reactive({
  count: 0,
});
const addCount = () => {
  state.count++;
};

//入力フォーム
const form = reactive({
  message: "Hello World",
});

const clickButton2 = () => {
  console.log(form.message);
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

  <!-- リストの表示 -->
  <p>{{ lan[0] }}</p>
  <p>{{ lan[1] }}</p>
  <p>{{ lan[2] }}</p>
  <p v-for="language in lanVfor" :key="language">{{ language }}</p>

  <ul>
    <li v-for="user in users" :key="user.id" class="list">
      {{ user.id }}:{{ user.name }}:{{ user.email }}
    </li>
  </ul>
  <div v-for="value in userobj" :key="value">{{ value }}</div>
  <div v-for="(value, name) in userobj" :key="value">
    {{ name }}:{{ value }}
  </div>

  <div v-for="userif in users" :key="userif.id">
    <div v-if="!userif.admin">{{ userif.name }}</div>
  </div>

  <!-- イベント設定 -->
  <button @click="clickButton('クリック成功')">click</button>
  <button @click="clickEvent($event)">クリック</button>

  <form @submit="send($event)">
    <button>送信(イベント修飾子)</button>
  </form>

  <form @submit.prevent="send2">
    <button @keyup.enter="submit">送信(キー修飾子)</button>
  </form>

  <!-- Reactivity -->
  <button type="button" @click="count++">count is {{ count }}</button>
  <button type="button" @click="addCount">count is {{ state.count }}</button>

  <!-- 入力フォーム -->
  <h2>入力フォーム</h2>
  <P>{{ form.message }}</P>
  <input v-model.lazy="form.message" />
  <div><button @click="clickButton2">Click</button></div>
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

.list {
  list-style: none;
}
</style>
