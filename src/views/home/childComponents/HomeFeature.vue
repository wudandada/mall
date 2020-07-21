<template>
  <div class="feature">
    <p class="feature-title">本周流行</p>
    <div class="feature-wrap">
      <div class="feature-item" v-for="item of recommends" :key="item.acm">
        <a :href="item.link">
          <img :src="item.image" alt />
          <p>{{item.title}}</p>
        </a>
      </div>
    </div>
    <div class="feature-wrap">
      <div class="feature-item" v-for="item of recommends" :key="item.acm">
        <a :href="item.link">
          <img :src="item.image" alt />
          <p>{{item.title}}</p>
        </a>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  components: {},
  name: 'HomeFeature',
  props: {
    recommends: {
      type: Array,
      default () {
        return []
      }
    }
  }
}
</script>
<style  scoped>
.feature-wrap {
  display: flex;
  padding: .15rem 0 .2rem;
}
.feature-title {
  display: block;
  width: 100%;
  line-height: .8rem;
  text-align: center;
  font-size: .34rem;
  font-weight: 550;
}
.feature-item {
  flex: 1;
  width: 25%;
  text-align: center;
  color: #666;
}
.feature-item img{
  width: 85%;
  margin-bottom: .15rem;
}
</style>
