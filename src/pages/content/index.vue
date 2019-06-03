<template>
  <div>
    <i-panel title="最新科技">
      <view>
        <view  v-for="item in data" :key="item">
         <view>{{item.text}}</view>
        </view>
     
       <text selectable>物联网教育及其应用</text>
       <text decode>股票&nbsp;大跌</text>
       <text decode>股票&nbsp;大跌</text>
      </view>
    </i-panel>
  </div>
</template>

<script>
import card from '@/components/card'

export default {
  data () {
    return {
      data:[]
      }
    },

    onLoad (option){
    console.log(option.type)
    this.data = require('@/data/' + option.type + '.json')
    },


  components: {
    card
  },

  methods: {
  },

  created () {
    // let app = getApp()
  }
}
</script>

<style>

</style>
