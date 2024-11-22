<template>
  <a :href="'catalog/' + this.data.id" class="card">
    <div class="preview">
      <img :src="this.data.image" alt="" />
    </div>
    <div class="title">
      <p>{{ this.data.title }}</p>
    </div>
    <div class="subtitle">
      <p>{{ this.platformCard.subtitle[this.getLang()] }}</p>
    </div>
  </a>
</template>

<script>
export default {
  mounted() {
    this.platformCard = this.data
    this.updatePlatformSubtitle()
  },
  props: {
    data: {
      type: Object,
      required: true,
    },
  },
  data() {
    return {
      platformCard: {},
    }
  },
  methods: {
    getLang() {
      return localStorage.getItem('lang')
    },
    updatePlatformSubtitle() {
      this.platformCard.subtitle = JSON.parse(this.data.subtitle)
    },
  },
  // watch: {
  //   getLang: {
  //     handler() {
  //       this.updatePlatformSubtitle()
  //     },
  //     immediate: true,
  //   },
  // },
}
</script>

<style scoped>
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
  margin-top: -10px;
}
</style>
