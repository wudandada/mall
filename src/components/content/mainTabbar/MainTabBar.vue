<template>
  <div id="tab-bar">
    <tab-bar>
      <tab-bar-item path="/home">
        <img src="@/assets/img/home.svg" alt slot="item-img" />
        <img src="@/assets/img/home_actived.svg" alt slot="item-img-actived" />
        <div slot="item-text">首页</div>
      </tab-bar-item>
      <tab-bar-item path="/category">
        <img src="@/assets/img/list.svg" alt slot="item-img" />
        <img src="@/assets/img/list_actived.svg" alt slot="item-img-actived" />
        <div slot="item-text">分类</div>
      </tab-bar-item>
      <tab-bar-item path="/shopCart">
        <img src="@/assets/img/car.svg" alt slot="item-img" />
        <img src="@/assets/img/car_actived.svg" alt slot="item-img-actived" />
        <div slot="item-text">购物车</div>
      </tab-bar-item>
      <tab-bar-item path="/profile">
        <img src="@/assets/img/profile.svg" alt slot="item-img" />
        <img src="@/assets/img/profile_actived.svg" alt slot="item-img-actived" />
        <div slot="item-text">我的</div>
      </tab-bar-item>
    </tab-bar>
  </div>
</template>

<script>
import TabBar from '../../common/tabbar/TabBar'
import TabBarItem from '../../common/tabbar/TabBarItem'
export default {
  components: {
    TabBar,
    TabBarItem
  },
  name: ''
}
</script>
