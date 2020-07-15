<template>
  <div class="tab-bar-item" @click="itemClick">
    <div v-if="!isActive"><slot name="item-img"></slot></div>
    <div v-else><slot name="item-img-actived"></slot></div>
    <div :style="activeStyle"><slot name="item-text"></slot></div>
  </div>
</template>

<script>
export default {
  name: 'TabBarItem',
  props: {
    path: String,
    colorActive: {
      type: String,
      default: '#fa4584'
    }
  },
  data () {
    return {
      // isActive: false
    }
  },
  methods: {
    itemClick () {
      this.$router.push(this.path)
    }
  },
  computed: {
    isActive () {
      return this.$route.path.indexOf(this.path) !== -1
    },
    activeStyle () {
      return this.isActive ? { color: this.colorActive } : {}
    }
  }
}
</script>
<style lang="stylus" scoped>
.tab-bar-item{
  flex 1
  text-align center
  color #666
  font-size .28rem
  margin-top .08rem
}
.tab-bar-item img{
  width .48rem
  margin-bottom .04rem
}

</style>
