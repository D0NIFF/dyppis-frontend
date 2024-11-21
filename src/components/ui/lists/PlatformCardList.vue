<template>
  <div class="card-list">
    <div class="platform-card" v-for="card in updatedData" :key="card.id">
      <a :href="'catalog/' + card.id" class="card">
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
</template>

<script>
export default {
  props: {
    data: {
      type: Array,
      required: true,
    },
  },
  data() {
    return {
      updatedData: this.getUpdatedData(),
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
      })
    },
    updateData() {
      this.updatedData = this.getUpdatedData()
    },
  },
  watch: {
    '$i18n.locale': {
      handler() {
        this.updateData()
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
</style>
