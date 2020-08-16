<template>
  <div class="search-result-tool-bar">
    <round-search-bar class="tool-bar" />
  </div>
</template>

<script>
import RoundSearchBar from '@/components/RoundSearchBar'
export default {
  components: {
    RoundSearchBar
  }
}
</script>

<style lang="scss" scoped>
@import '../assets/scss/_variables';
.search-result-tool-bar {
  border-bottom: 1px solid map-get($map: $colors, $key: 'grey');
  padding-bottom: 20px;
  .tool-bar {
    margin-top: map-get($map: $margins, $key: 'big');
    margin-left: map-get($map: $margins, $key: 'medium');
  }
}
</style>
