<template>
  <div class="home">
    <div class="search-plane">
      <my-search-logo class="my-search-logo" />
      <search-bar class="search-input" />
    </div>
  </div>
</template>

<script>
import MySearchLogo from '@/components/MySearchLogo'
import SearchBar from '@/components/SearchBar'
export default {
  components: {
    MySearchLogo,
    SearchBar
  }
}
</script>

<style lang="scss" scoped>
.search-plane {
  text-align: center;
  .my-search-logo {
    margin-top: 120px;
    margin-bottom: 50px;
  }
  .search-input {
    margin: 0 auto;
  }
}
</style>
