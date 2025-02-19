<script setup lang="ts">
import '@/assets/style/common/index.scss'
import { RouterView } from 'vue-router'
import Header from './components/Global/Header.vue'
</script>
<template>
  <div>
    <Header />
    <RouterView />
  </div>
</template>
