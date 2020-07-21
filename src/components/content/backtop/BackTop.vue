<template>
  <div class="back-top">
    <img src="../../../assets/img/backtop.png" alt="">
  </div>
</template>

<script>
export default {
  components: {},
  name: 'BackTOp',
  props: {},
  data () {
    return {
    }
  }
}
</script>
<style scoped>
.back-top {
  position: fixed;
  z-index: 9;
  right: 15px;
  bottom: 60px;
  background: #fff;
  width: 36px;
  height: 36px;
  border-radius: 50% 50%;
}
.back-top img{
  display: block;
  width: 100%;
}
</style>
