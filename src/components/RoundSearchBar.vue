<template>
  <div class="round-search-bar">
    <img
      src="../assets/mysearch_logo_small.png"
      alt="logo"
      class="logo"
      @click="$router.push('/')"
    />
    <div class="input-plane">
      <input
        type="text"
        class="input-search"
        v-model="searchText"
        @keyup.enter="doSearch"
      />
      <button class="btn-search" @click="doSearch">
        <i class="iconfont icon-search"></i>
      </button>
    </div>
  </div>
</template>

<script>
export default {
  created() {
    this.searchText = this.$route.params.searchText
  },
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
.round-search-bar {
  display: flex;
  align-items: center;
  .logo {
    width: 230px;
    height: 47px;
    cursor: pointer;
  }
  .input-plane {
    width: 500px;
    border: 1px solid map-get($map: $search, $key: 'border-color');
    border-radius: 20px;
    margin-left: map-get($map: $margins, $key: 'big');
    height: map-get($map: $round-search, $key: 'height');
    &:focus-within {
      box-shadow: 0 1px 6px 0 rgba(32, 33, 36, 0.1);
    }
    &:hover {
      box-shadow: 0 1px 6px 0 rgba(32, 33, 36, 0.1);
    }

    .input-search {
      border: none;
      width: 88%;
      margin-left: 15px;
      font-size: 1em;
    }
    .btn-search {
      border: none;
      height: 40px;
      background-color: #fff;
      line-height: map-get($map: $round-search, $key: 'height');
      color: map-get($map: $colors, $key: 'blue');
      cursor: pointer;
    }
  }
}
</style>
