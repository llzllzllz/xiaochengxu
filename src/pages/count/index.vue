<template>
  <div class="counter-warp">
    <image src="/static/images/account.png" class="image"></image>
    <view class="boxs">
    <i-row>
      <i-col span="24" i-class="col-class">签到次数：{{ type }}</i-col></i-row>  
    <i-row>
    <i-col span="24"><button @click="increments" hover-class="hover" type="primary">签到</button></i-col>
    </i-row>  
    </view>
  </div>
</template>

<script>
// Use Vuex
import card from '@/components/card'
import store from './store'

export default {
  components: {
    card
  },

  data () {
    return {
      type: 0
      }
  },
  computed: {
    count () {
      return store.state.count
    }
  },

  methods: {
    increments () {
      if (this.type == 0){
        this.type += 1
        wx.showToast({
          title: '签到成功',
          icon: 'none',
          duration: 2000
        })
        } 
      else{
        wx.showToast({
          title: '已签到',
          icon: 'none',
          duration: 2000
        })
      }
    },
    increment () {
      store.commit('increment')
    },
    decrement () {
      store.commit('decrement')
    }
  }
}
</script>

<style>
.boxs {
  margin-top: 10px;
}
.image {
  width: 50px;
  height: 50px;
}
.counter-warp {
  text-align: center;
  margin-top: 10px;
}
.home {
  display: inline-block;
  margin: 100px auto;
  padding: 5px 10px;
  color: blue;
  border: 1px solid blue;
}
.hover {
  background-color: aquared;

}
.col-class {
  border: 1px solid #98bf21;
  height: 30pt;
  text-align: center;
}
</style>
