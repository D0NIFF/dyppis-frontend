<script setup lang="ts">
import LanguageSelector from '@/components/ui/dropdowns/LanguageSelector.vue'
</script>

<template>
  <main>
    <!-- <SearchInput :placeholder="$t('header.search')"></SearchInput>
    <IconButton :src="'images/icons/search-icon.svg'" :onclick="test"></IconButton> -->
    <LanguageSelector></LanguageSelector>
  </main>
</template>

<script lang="ts">
export default {
  methods: {
    test() {
      console.log('test')
    },
  },
}
</script>
