<script setup>
import { RouterLink, RouterView } from 'vue-router'
import CustomHeader from './components/customHeader.vue';
</script>

<template>
  <header>
    <div class="wrapper">
      <nav>
      </nav>
    </div>
  </header>
  <CustomHeader></CustomHeader>

  <RouterView />
</template>
