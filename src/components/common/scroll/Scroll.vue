<template>
  <div class="wrapper" ref="wrapper">
    <div class="content">
      <slot></slot>
    </div>
  </div>
</template>

<script>
import BScroll from 'better-scroll'
export default {
  components: {},
  name: 'Scroll',
  props: {
    probeType: {
      type: Number,
      default () {
        return 0
      }
    },
    pullUpLoad: {
      type: Boolean,
      default () {
        return 0
      }
    }
  },
  data () {
    return {
      scroll: null
    }
  },
  mounted () {
    // 创建滚动事件
    this.scroll = new BScroll(this.$refs.wrapper, {
      click: true,
      probeType: this.probeType,
      pullUpLoad: this.pullUpLoad
    })
    // 监听滚动的位置
    if (this.probeType === 2 || this.probeType === 3) {
      this.scroll.on('scroll', position => {
        this.$emit('scrollControl', position)
      })
    }

    // 监听上拉事件
    this.scroll.on('pullingUp', () => {
      this.$emit('pullingUp')
    })
  },
  methods: {
    scrollTop (x, y, time) {
      this.scroll && this.scroll.scrollTo(x, y, time)
    },
    finishPullUp () {
      this.scroll && this.scroll.finishPullUp()
    },
    refresh () {
      this.scroll && this.scroll.refresh()
    }
  }
}
</script>
<style lang="scss" scoped>
</style>
