<template>
  <div>
    <div class="tab-bar">
      <slot></slot>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Tabbar'
}
</script>
<style lang="stylus" scoped>
.tab-bar{
  display flex
  position fixed
  left 0
  right 0
  bottom 0
  height .98rem
  background-color #f6f6f6
  box-shadow 0 -2px rgba(1,1,1,0.04)
}

</style>
