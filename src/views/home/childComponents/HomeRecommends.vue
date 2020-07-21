<template>
  <div class="recommends">
    <div class="recommends-item" v-for= "item of recommends" :key="item.acm">
      <a :href="item.link">
        <img :src="item.image" alt="">
        <p>{{item.title}}</p>
      </a>
    </div>
  </div>
</template>

<script>
export default {
  components: {},
  name: 'HomeRecommends',
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
<style scoped>
.recommends {
  display: flex;
  padding: .2rem 0 .5rem;
  border-bottom: .2rem solid #eee;
}
.recommends-item {
  flex: 1;
  width: 25%;
  text-align: center;
  color: #666;
}
.recommends-item img{
  width: 85%;
  margin-bottom: .15rem;
}
</style>
