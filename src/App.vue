<!-- eslint-disable @typescript-eslint/no-unused-vars -->
<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
import { useI18n } from 'vue-i18n'

const { t, locale } = useI18n({ useScope: 'global' })
import Header from '@/components/layouts/Header.vue'
</script>

<template>
  <Header></Header>
  <RouterView />
</template>

<style scoped></style>
