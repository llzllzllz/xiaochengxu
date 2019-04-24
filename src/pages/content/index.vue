<template>
  <div>
    <i-panel title="最新科技">
      <view>
       <h1></h1>
       <p>智能城市</p>
       <p>语音AI</p>
       <p>AI专用芯片</p>
       <p>图神经网络系统</p>
       <p>5G</p>
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
