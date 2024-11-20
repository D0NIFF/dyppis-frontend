<script setup>
import Logo from '@/components/ui/elements/Logo.vue'
import SearchForm from '@/components/ui/forms/SearchForm.vue'
import LanguageSelector from '@/components/ui/dropdowns/LanguageSelector.vue'
</script>
<template>
  <header>
    <div class="top-block">
      <div class="logo-item">
        <Logo></Logo>
      </div>
      <nav>
        <div class="search-block">
          <SearchForm></SearchForm>
        </div>
        <div class="login-block">
          <LanguageSelector></LanguageSelector>
        </div>
      </nav>
    </div>
    <div class="bottom-block"></div>
  </header>
</template>

<style scoped></style>

<script>
export default {
  data() {
    return {
      test: 0,
    }
  },
  methods: {
    up() {
      this.test += 1
    },
  },
}
</script>

<style scoped>
header {
  width: 100%;
}
header .top-block {
  width: 100%;
  height: 100px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  border-bottom: 1px solid var(--light-blue);
}
header nav {
  display: flex;
  flex-basis: 80%;
}
header nav .search-block {
  flex-basis: 60%;
}
</style>
