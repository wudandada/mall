<template>
  <div class="goods-item">
    <img :src="goodsItem.show.img" alt="" @load="imageLoad">
    <div class="item-info">
      <p>{{goodsItem.title}}</p>
      <span class="item-price">{{goodsItem.price}}</span>
      <span class="item-collect">{{goodsItem.cfav}}</span>
    </div>
  </div>
</template>

<script>
export default {
  components: {},
  name: 'GoodsListItem',
  props: {
    goodsItem: {
      type: Object,
      default () {
        return {}
      }
    }
  },
  methods: {
    imageLoad () {
      this.$bus.$emit('itemImageLoad')
    }
  }
}
</script>
<style scoped>
.goods-item{
  width: 48%;
  margin-bottom: 10px;
}
.goods-item img {
  width: 100%;
  border-radius: 3px;
}
.item-info {
  text-align: center;
  margin-top: 5px;
}
.item-info p{
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
  margin-bottom: 3px;
}
.item-price {
  color: #ff8198;
  margin-right: 28px;
}
.item-collect {
  position: relative;
}
.item-collect::before{
  content: '';
  position: absolute;
  left: -17px;
  top: 0px;
  width: 16px;
  height: 16px;
  background: url('../../../../src/assets/img/collect.svg') 0 0/ 14px 14px no-repeat ;
}
</style>
