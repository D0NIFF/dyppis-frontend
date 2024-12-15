<script setup>
import PrimaryButton from '@/components/ui/buttons/PrimaryButton.vue';
</script>
<template>
  <div class="card-list">
    <div class="platform-card" v-for="card in updatedData" :key="card.id">
      <a :href="'/catalog/' + this.$route.params.type + '/' + card.slug" class="card">
        <div class="preview">
          <img :src="card.image" alt="" />
        </div>
        <div class="title">
          <p>{{ card.title }}</p>
        </div>
        <div class="subtitle">
          <p>{{ card.subtitle[getLang()] }}</p>
        </div>
      </a>
    </div>
  </div>
  <div class="load-more" v-if="isLoadMore">
      <PrimaryButton :onclick="loadMore">{{ $t('button.see-more') }}</PrimaryButton>
    </div>
</template>

<script>
export default {
  props: {
    data: {
      type: Array,
      required: true,
    },
    isLoadMore: {
      type: Boolean,
      default: false,
      required: false,
    },
    apiUrl: {
      type: String,
      required: false,
    }
  },
  data() {
    return {
      updatedData: this.getUpdatedData(),
      currentPage: 1,
      itemsPerPage: 10,
      hasMore: true,
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
  methods: {
    getLang() {
      return localStorage.getItem('lang') || 'en'
    },
    getUpdatedData() {
      return this.data.map((item) => {
        if (typeof item.subtitle === 'string') {
          item.subtitle = JSON.parse(item.subtitle)
        }
        return item
      }).slice(0, this.currentPage * this.itemsPerPage);
    },
    updateData() {
      this.updatedData = this.getUpdatedData();
    },
    async loadMore() {
      // Здесь вы можете сделать запрос к вашему API для получения дополнительных площадок
      // const newData = await this.fetchMoreData();
      // // eslint-disable-next-line vue/no-mutating-props
      // this.data.push(...newData);
      // this.currentPage++;
      // this.updateData();
      // this.hasMore = newData.length > 0; // Проверяем, есть ли еще данные


      // eslint-disable-next-line vue/no-mutating-props
      this.data.push(this.platformCards[0]);
      // eslint-disable-next-line vue/no-mutating-props
      this.data.push(this.platformCards[1]);
      // eslint-disable-next-line vue/no-mutating-props
      this.data.push(this.platformCards[2]);
      // eslint-disable-next-line vue/no-mutating-props
      this.data.push(this.platformCards[3]);
      this.currentPage++;
      this.updateData();
    },
    async fetchMoreData() {
      // Пример запроса к API
      const response = await fetch(`https://api.example.com/platforms?page=${this.currentPage + 1}`);
      const data = await response.json();
      return data.platforms; // Предполагаем, что API возвращает массив площадок
    },
  },
  watch: {
    '$i18n.locale': {
      handler() {
        this.updateData();
      },
      immediate: true,
    },
  },
}
</script>

<style scoped>
.card-list {
  width: 100%;
  display: flex;
  flex-flow: wrap;
  grid-gap: 10px;
}

.card {
  width: 150px;
  height: 150px;
  display: flex;
  flex-flow: wrap;
  justify-content: center;
  align-items: center;
  background-color: transparent;
  border: 3px solid transparent;
  border-radius: 5px;
  background-image: linear-gradient(var(--dark-light-background), var(--dark-light-background)),
    linear-gradient(to right, var(--light-lime), var(--light-blue));
  background-origin: border-box;
  background-clip: content-box, border-box, padding-box;
  text-decoration: none;
  transition: 0.1s ease-in-out;
}
.card:hover {
  margin-top: -10px;
}
.preview {
  width: 40%;
  margin-top: 5px;
}
.preview img {
  width: 100%;
}
.title {
  width: 100%;
  color: white;
  text-align: center;
  font-family: var(--default-font);
  font-weight: 600;
  font-size: 18px;
}
.subtitle {
  width: 100%;
  color: white;
  text-align: center;
  font-family: var(--default-font);
  font-weight: 400;
  font-size: 12px;
  margin-top: -15px;
}
.load-more {
  width: 300px;
  height: 45px;
  margin: 20px auto;
}

</style>
