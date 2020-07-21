<template>
  <div class="wrapper">
    <swiper>
      <swiper-item v-for="item of banners" :key="item.acm">
        <a :href="item.link">
          <img :src="item.image" alt="" @load="imgLoad">
        </a>
      </swiper-item>
    </swiper>
  </div>
</template>

<script>
import { Swiper, SwiperItem } from '../../../components/common/swiper/index'
export default {
  name: 'HomeSwipers',
  props: {
    banners: {
      type: Array,
      default () {
        return []
      }
    }
  },
  data () {
    return {
      isLoadImg: false
    }
  },
  components: {
    Swiper,
    SwiperItem
  },
  methods: {
    imgLoad () {
      if (!this.isLoadImg) {
        this.$emit('swiperImgLoad')
        this.isLoadImg = true
      }
    }
  }
}
</script>
<style>

</style>
