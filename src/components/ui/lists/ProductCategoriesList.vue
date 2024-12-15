<template>
  <div class="carousel">
    <button @click="prev" class="carousel-button">←</button>
    <div class="carousel-container" @wheel="handleScroll">
      <a
        v-for="category in visibleCategories"
        :key="category.slug"
        :href="'/catalog/' + category.slug"
        class="carousel-item"
      >
        <img
          :src="`${category.image.category.url}/${category.image.file_name}`"
          :alt="category.title[getLang()]"
        />
        <p>{{ category.title[getLang()] }}</p>
      </a>
    </div>
    <button @click="next" class="carousel-button">→</button>
  </div>
</template>

<script>
export default {
  props: {
    data: {
      type: Array,
      required: true
    }
  },
  data() {
    return {
      categories: [], // Здесь должны быть ваши данные
      currentIndex: 0,
      itemsToShow: 3, // Количество элементов, отображаемых одновременно
    };
  },
  computed: {
    visibleCategories() {
      return this.data.slice(this.currentIndex, this.currentIndex + this.itemsToShow);
    },
  },
  watch: {
    getLang: {
      handler() {
        this.updateCategories()
      },
      immediate: true,
    },
  },
  methods: {
    next() {
      if (this.currentIndex < this.data.length - this.itemsToShow) {
        this.currentIndex++;
      }
    },
    prev() {
      if (this.currentIndex > 0) {
        this.currentIndex--;
      }
    },
    handleScroll(event) {
      if (event.deltaY > 0) {
        this.next();
      } else {
        this.prev();
      }
      event.preventDefault();
    },
    updateCategories() {
      this.data.forEach((item) => {
        item.title = JSON.parse(item.title);
      })
    },
    getLang() {
      return localStorage.getItem('lang')
    },
  },

};
</script>

<style scoped>
.carousel {
  display: flex;
  align-items: center;
}
.carousel-container {
  display: flex;
  gap: 10px;
  overflow: hidden;
  width: 100%; /* Установите ширину по вашему усмотрению */
}
.carousel-item {
  padding: 10px 20px;
  text-decoration: none;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 7px;
  background-color: var(--dark-light-background);
  font-family: var(--default-font);
  font-size: 14px;
  font-weight: 600;
  color: white;
}
.carousel-item img {width: 25px;}
.carousel-button {
  cursor: pointer;
}
</style>
