<template>
  <div>
    <search-result-item :list="list" :searchText="searchText" />
  </div>
</template>

<script>
import SearchResultItem from '@/components/SearchResultItem'
export default {
  props: {
    searchText: String
  },
  created() {
    this.getSearchList()
  },
  data() {
    return {
      list: []
    }
  },
  methods: {
    async getSearchList() {
      const { data: res } = await this.$http.get('/data.json')
      this.list = Object.entries(res)
        .reduce((result, [key, value]) => {
          if (key.includes(this.searchText) || this.searchText.includes(key)) {
            result.push(value)
          }
          return result
        }, [])
        .flat()

      console.log(this.list)
    }
  },
  components: {
    SearchResultItem
  }
}
</script>

<style lang="scss" scoped></style>
