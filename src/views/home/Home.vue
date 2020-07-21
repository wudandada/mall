<template>
  <div class="home">
    <nav-bar class="home-nav">
      <div slot="center">购物街</div>
    </nav-bar>
    <tab-control
      :tab-titles="tabTitles"
      @tabClick="tabClick"
      ref="tabControl1"
      v-show="isShowTab"
      class="topTab"
    ></tab-control>
    <scroll
      class="content"
      ref="scroll"
      :probe-type="3"
      @scrollControl="contenScroll"
      :pull-up-load="true"
      @pullingUp="loadMore"
    >
      <home-swiper :banners="banners" @swiperImgLoad="swiperImgLoad"></home-swiper>
      <home-recommends :recommends="recommends"></home-recommends>
      <home-feature :recommends="recommends"></home-feature>
      <tab-control
        :tab-titles="tabTitles"
        @tabClick="tabClick"
        ref="tabControl2"
      ></tab-control>
      <goods-list :goods="goods[currentType].list"></goods-list>
    </scroll>
    <back-top @click.native="backClick" v-show="isShowBackTop"></back-top>
  </div>
</template>

<script>
// 子组件
import HomeSwiper from './childComponents/HomeSwiper'
import HomeRecommends from './childComponents/HomeRecommends'
import HomeFeature from './childComponents/HomeFeature'

// 公共组件
import NavBar from '@/components/common/navbar/NavBar'
import TabControl from '@/components/content/tabcontrol/TabControl'
import GoodsList from '@/components/content/goods/GoodsList'
import BackTop from '@/components/content/backtop/BackTop'

import { getHomeMultidata, getHomeGoods } from '@/network/home.js'
import { debounce } from '../../common/utils'

import Scroll from '@/components/common/scroll/Scroll'

export default {
  name: 'Home',
  components: {
    HomeSwiper,
    HomeRecommends,
    HomeFeature,
    NavBar,
    TabControl,
    GoodsList,
    Scroll,
    BackTop
  },
  data () {
    return {
      banners: [],
      recommends: [],
      tabTitles: [
        {
          id: '0001',
          title: '流行'
        },
        {
          id: '0002',
          title: '新款'
        },
        {
          id: '0003',
          title: '精选'
        }
      ],
      goods: {
        pop: { page: 0, list: [] },
        new: { page: 0, list: [] },
        sell: { page: 0, list: [] }
      },
      currentType: 'pop',
      isShowBackTop: false,
      tabOffsetTop: 0,
      isShowTab: false
    }
  },
  created () {
    this.getHomeMultidata()

    this.getHomeGoods('pop')
    this.getHomeGoods('new')
    this.getHomeGoods('sell')
  },
  mounted () {
    const refresh = debounce(this.$refs.scroll.refresh, 100)
    this.$bus.$on('itemImageLoad', () => {
      refresh()
    })
  },
  methods: {
    // 事件监听

    tabClick (index) {
      switch (index) {
        case 0:
          this.currentType = 'pop'
          break
        case 1:
          this.currentType = 'new'
          break
        case 2:
          this.currentType = 'sell'
          break
      }
      this.$refs.tabControl1.currentIndex = index
      this.$refs.tabControl2.currentIndex = index
    },
    // 返回顶部
    backClick () {
      this.$refs.scroll.scrollTop(0, 0, 300)
    },
    // 是否显示返回顶部
    contenScroll (positon) {
      this.isShowBackTop = (-positon.y) > 1000
      this.isShowTab = (-positon.y) > this.tabOffsetTop
    },
    // 上拉加载更多
    loadMore () {
      this.getHomeGoods(this.currentType)
    },
    debounce (func, delay) {
      let timer = null
      return function (...args) {
        if (timer) clearTimeout(timer)
        timer = setTimeout(() => {
          func.apply(this, args)
        }, delay)
      }
    },
    swiperImgLoad () {
      this.tabOffsetTop = this.$refs.tabControl2.$el.offsetTop
    },
    // 网络请求
    getHomeMultidata () {
      getHomeMultidata().then(res => {
        this.banners = res.data.banner.list
        this.recommends = res.data.recommend.list
      })
    },
    getHomeGoods (type) {
      const page = this.goods[type].page + 1
      getHomeGoods(type, page).then(res => {
        this.goods[type].list.push(...res.data.list)
        this.goods[type].page += 1
        this.$refs.scroll.finishPullUp()
      })
    }
  }
}
</script>
<style scoped>
.home {
  /* padding-top: 44px; */
  position: relative;
  height: 100vh;
}

.home-nav {
  background-color: #ff8198;
  color: #fff;
  /* position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 2; */
}
.content {
  position: absolute;
  overflow: hidden;
  top: 44px;
  bottom: 49px;
  right: 0;
  left: 0;
}
.topTab {
  position: relative;
  z-index: 9;
}
/* .content {
    height: calc(100% - 93px);
    overflow: hidden;
    margin-top: 44px;
  } */
</style>
