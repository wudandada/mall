<template>
  <div class="nav-bar">
    <div class="left"><slot name="left"></slot></div>
    <div class="center"><slot name="center"></slot></div>
    <div class="right"><slot name="right"></slot></div>
  </div>
</template>

<script>
export default {
  components: {},
  name: 'Nav'
}
</script>
<style lang="stylus" scoped>
.nav-bar {
  display flex
  height .88rem
  line-height .88rem
  width 100%
  text-align center
}
.left {
  flex: 1
}
.center {
  flex: 6
}
.right {
  flex: 1
}
</style>
