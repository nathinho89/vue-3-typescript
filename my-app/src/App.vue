<script setup lang="ts">
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://v3.vuejs.org/api/sfc-script-setup.html#sfc-script-setup
import { reactive } from "vue";
import Counter from "./components/Counter.vue";

interface AppInfo {
  name: string;
  slogan: string;
}

const appInfo: AppInfo = reactive({
  name: "Counter",
  slogan: "An app you can count on",
});
</script>

<template>
  <div>
    <h1>{{ appInfo.name }}</h1>
    <h2>{{ appInfo.slogan }}</h2>
  </div>
  <Counter limit="10" :alert-message-on-limit="'Count limit has been reached'">
  </Counter>
</template>
