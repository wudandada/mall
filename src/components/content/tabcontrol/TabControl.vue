<template>
  <div class="tabcontrol">
    <div
      class="tab-item"
      v-for = "(item, index) in tabTitles"
      :key="item.id"
      :class="{active:index === currentIndex}"
      @click="itemClick(index)"
    >
      <span>{{item.title}}</span>
    </div>
  </div>
</template>

<script>
export default {
  components: {},
  name: '',
  props: {
    tabTitles: {
      type: Array,
      default () {
        return []
      }
    }
  },
  data () {
    return {
      currentIndex: 0
    }
  },
  methods: {
    itemClick (index) {
      this.currentIndex = index
      this.$emit('tabClick', index)
    }
  }
}
</script>
<style scoped>
  .tabcontrol{
    display: flex;
    height: 40px;
    line-height: 40px;
    background-color: #fff;
  }
  .tab-item{
    flex: 1;
    text-align: center;
    box-sizing: border-box;
  }
  .tab-item span{
    padding: 5px 5px 3px;
  }
  .active {
    color: #ff8198
  }
  .active span{
    border-bottom: 2px solid #ff8198
  }
</style>
