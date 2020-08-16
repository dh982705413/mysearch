<template>
  <div class="search-result-item">
    <div class="tip">MySearch为您找到的结果有{{ count }}条</div>
    <div class="result-item" v-for="item in showList" :key="item.title">
      <a class="title">{{ item.title }}</a>
      <a :href="item.url" class="link">{{ item.url }}</a>
      <div class="desc" v-html="item.desc"></div>
      <div class="time">{{ item.date }}</div>
    </div>
    <div class="noData" v-show="isShow">
      没有符合条件的结果
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {}
  },
  props: {
    list: Array,
    searchText: String
  },
  computed: {
    showList() {
      return this.list.map(item => {
        item.desc = item.desc.replace(
          this.searchText,
          `<span style="color:red">${this.searchText}</span>`
        )
        return item
      })
    },
    isShow() {
      return this.list.length === 0
    },
    count() {
      return this.list.length
    }
  }
}
</script>

<style lang="scss" scoped>
@import '../assets/scss/_variables';
.search-result-item {
  width: 700px;
  margin-left: 20px;
  .tip {
    color: #999999;
    margin: 5px 0;
  }
  .result-item {
    display: flex;
    flex-flow: column wrap;
    margin-bottom: 30px;
    cursor: pointer;
    .title {
      font-size: 1.3em;
      color: map-get($map: $colors, $key: 'blue');
      cursor: pointer;
    }
    .link {
      margin: 5px 0;
      color: map-get($map: $colors, $key: 'green');
    }
    .desc {
      word-break: break-all;
    }
    .time {
      text-align: right;
      color: map-get($map: $colors, $key: 'grey');
    }
  }
}
</style>
