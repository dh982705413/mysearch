<template>
  <div class="search-bar">
    <input
      type="text"
      class="input-search"
      v-model="searchText"
      @keyup.enter="doSearch"
    />
    <button class="btn-search" @click="doSearch">
      <slot name="btnText">
        搜索一下
      </slot>
    </button>
  </div>
</template>

<script>
export default {
  name: 'my-search-bar',

  data() {
    return {
      searchText: ''
    }
  },

  methods: {
    doSearch() {
      if (this.searchText !== '') {
        this.$router.push(`/search/${this.searchText}`)
      }
    }
  }
}
</script>

<style lang="scss" scoped>
@import '../assets/scss/_variables.scss';

.search-bar {
  max-width: 700px;
  .input-search {
    width: 75%;
    height: map-get($map: $search, $key: 'height');
    font-size: 1.2em;
    vertical-align: bottom;
    border: 1px solid map-get($map: $search, $key: 'border-color');
    border-right: none;
    padding-left: 10px;
    border-top-left-radius: map-get($map: $search, $key: 'input-radius');
    border-bottom-left-radius: map-get($map: $search, $key: 'input-radius');
    &:hover {
      border-color: map-get($map: $colors, $key: 'blue');
    }
    &:focus {
      border-color: map-get($map: $colors, $key: 'blue');
    }
  }
  .btn-search {
    width: 25%;
    height: map-get($map: $search, $key: 'height');
    background-color: map-get($map: $search, $key: 'btn-color');
    color: map-get($map: $search, $key: 'font-color');
    font-size: 1.5em;
    border: none;
    border-top-right-radius: map-get($map: $search, $key: 'btn-radius');
    border-bottom-right-radius: map-get($map: $search, $key: 'btn-radius');
    cursor: pointer;
    &:hover {
      opacity: 0.9;
    }
  }
}
</style>
