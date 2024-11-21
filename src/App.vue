<!-- eslint-disable @typescript-eslint/no-unused-vars -->
<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
import { useI18n } from 'vue-i18n'

const { t, locale } = useI18n({ useScope: 'global' })
import Header from '@/components/layouts/Header.vue'
</script>

<template>
  <Header></Header>
  <div class="content">
    <RouterView />
  </div>
</template>

<style scoped>
.container {
  width: 100%;
  min-height: 100vh;
  margin-top: 200px;
  background-color: var(--dark-background);
}

.container {
  max-width: 1200px;
  margin-left: auto;
  margin-right: auto;
}

@media only screen and (max-width: 1000px) {
  .container {
    margin-top: 240px;
  }
}
@media only screen and (max-width: 500px) {
  .container {
    margin-top: 260px;
  }
}
</style>
