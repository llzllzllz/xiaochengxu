<template>
  <div>
   <!--  <i-panel title="最新科技">
      <view>
        <view  v-for="item in data" :key="item">
         <view>{{item.text}}</view>
        </view>
      </view>
    </i-panel> -->
    <i-panel title="最新科技">
     <i-swipeout v-for="item in text" :key="item">
       <view slot="content">
         <i-cell-group>
        <i-cell :title="item.title"  :label="item.label"></i-cell>
      </i-cell-group>
       </view>
       
       <view slot="button" class="i-swipeout-demo-button-group">
            <view class="i-swipeout-demo-button">点赞</view>
            <view class="i-swipeout-demo-button">分享</view>
            <view class="i-swipeout-demo-button">删除</view>
        </view>
     </i-swipeout>
    </i-panel>


     
  </div>
</template>

<script>
import card from '@/components/card'

export default {
  data () {
    return {
      text: [
      {title: '5G',label:'科5G网络是否符合大众需求'},
      {title: '传人人车',label:'传人人车裁员比例达到60%',},
      {title: '华为鸿蒙',label:'中国制造的系统何时能发布，效用能使大众满意吗',},
      {title: '格力与奥克斯',label:'霸主为何相争，其中存在怎样的矛盾'},
      {title: '搜狐进入社交圈',label:'搜狐参与社交之战，一场声扬还是目的策划',},
      {title: '字节跳动',label:'字节跳动组建团队建立重度游戏，怎么看待',},
      ],
      // data:[]
      }
    },

    /* onLoad (option){
    console.log(option.type)
    this.data = require('@/data/' + option.type + '.json')
    }, */


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
