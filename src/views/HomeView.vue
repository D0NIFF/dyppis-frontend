<script setup lang="ts">
import Carousel from '@/components/ui/media/Carousel.vue'
import PlatformCardList from '@/components/ui/lists/PlatformCardList.vue'
</script>

<template>
  <div class="banner-carousel">
    <Carousel :images="images" :autoPlay="true"></Carousel>
  </div>
  <div class="platforms-list">
    <PlatformCardList :data="platformCards" />
  </div>
</template>

<script lang="ts">
export default {
  data() {
    return {
      platformTypes: [],
      images: [
        '/images/banners/preview1.jpg',
        '/images/banners/preview2.jpg',
        '/images/banners/preview3.jpg',
        '/images/banners/preview4.jpeg',
        '/images/banners/banner1.jpg',
      ],
      platformCards: [
        {
          id: '1',
          image: 'images/platforms/steam.svg',
          title: 'Steam',
          subtitle:
            '{"de": "Software", "en": "Software", "es": "Software", "fr": "Logiciel", "it": "Software", "ru": "Программное обеспечение"}',
        },
        {
          id: '2',
          image: 'images/platforms/microsoft.svg',
          title: 'Microsoft',
          subtitle:
            '{"de": "Software", "en": "Software", "es": "Software", "fr": "Logiciel", "it": "Software", "ru": "Программное обеспечение"}',
        },
        {
          id: '3',
          image: 'images/platforms/steam.svg',
          title: 'Steam',
          subtitle:
            '{"de": "Software", "en": "Software", "es": "Software", "fr": "Logiciel", "it": "Software", "ru": "Программное обеспечение"}',
        },
        {
          id: '4',
          image: 'images/platforms/microsoft.svg',
          title: 'Microsoft',
          subtitle:
            '{"de": "Software", "en": "Software", "es": "Software", "fr": "Logiciel", "it": "Software", "ru": "Программное обеспечение"}',
        },
      ],
    }
  },
  methods: {
    getLang() {
      return localStorage.getItem('lang')
    },
  },
}
</script>

<style scoped>
.banner-carousel {
  width: 100%;
}
.platforms-list {
  margin-top: 50px;
}
</style>
