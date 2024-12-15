<script setup>
import LetterList from '@/components/ui/lists/LetterList.vue';
import PlatformList from '@/components/ui/lists/PlatformList.vue';
</script>
<template>
  <div class="letters-block">
    <LetterList></LetterList>
  </div>
  <div class="cards-block">
    <PlatformList :data="platformCards" :isLoadMore="true" />
  </div>
</template>

<script>
export default {
  data() {
    return {
      platformCards: [
        {
          id: '1',
          slug: 'steam',
          image: '/images/platforms/steam-logo.svg',
          title: 'Steam',
          subtitle:
            '{"de": "Software", "en": "Software", "es": "Software", "fr": "Logiciel", "it": "Software", "ru": "Программное обеспечение"}',
        },
        {
          id: '2',
          slug: 'microsoft',
          image: '/images/platforms/microsoft-logo.svg',
          title: 'Microsoft',
          subtitle:
            '{"de": "Software", "en": "Software", "es": "Software", "fr": "Logiciel", "it": "Software", "ru": "Программное обеспечение"}',
        },
        {
          id: '3',
          slug: 'epic-games',
          image: '/images/platforms/epic-games-logo.svg',
          title: 'Epic Games',
          subtitle:
            '{"de": "Software", "en": "Software", "es": "Software", "fr": "Logiciel", "it": "Software", "ru": "Программное обеспечение"}',
        },
        {
          id: '4',
          slug: 'origin',
          image: '/images/platforms/origin-logo.svg',
          title: 'Origin',
          subtitle:
            '{"de": "Software", "en": "Software", "es": "Software", "fr": "Logiciel", "it": "Software", "ru": "Программное обеспечение"}',
        },
      ],
    }
  },
}
</script>

<style>
.cards-block {
  margin-top: 20px;
}
</style>
