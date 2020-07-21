<template>
  <div class="goods-list">
    <goods-list-item
    v-for="item of goods"
    :key="item.acm"
    :goodsItem="item"
    >
    </goods-list-item>
  </div>
</template>

<script>
import GoodsListItem from './GoodsLIstItem'
export default {
  components: {
    GoodsListItem
  },
  name: 'GoodsList',
  props: {
    goods: {
      type: Array,
      default () {
        return []
      }
    }
  }
}
</script>
<style scoped>
.goods-list {
  width: 100%;
  display: flex;
  flex-wrap: wrap;
  justify-content: space-evenly;
}
</style>
