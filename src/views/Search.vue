<template>
  <div class="search">
    <search-result-tool-bar />
    <search-result :searchText="searchText" />
  </div>
</template>
<script>
import SearchResult from '@/components/SearchResult'
import SearchResultToolBar from '@/components/SearchResultToolBar'
export default {
  components: {
    SearchResultToolBar,
    SearchResult
  },
  computed: {
    searchText() {
      return this.$route.params.searchText
    }
  }
}
</script>
