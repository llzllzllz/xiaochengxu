<template>
  <div>
      <swiper :indicator-dots="indicatorDots"
      :autoplay="autoplay"
      :interval="interval"
      :duration="duration"
      :indicator-color="indicatorcolor"
      :indicator-active-color="activecolor"
       circular>
        <block v-for="item in imgUrls" :key="item">
        <swiper-item>
          <image :src="item.img"  mode="widthfix"/>
        </swiper-item>
        </block>
    </swiper>
    <view>
      <view v-for="item in arr" :key="item">
      {{index}}:{{item}}
    </view>
      <block v-for="item in arr" :key="item">
      {{index}}:{{item}}
    </block>
    </view>

    <ul class="container log-list">
      <li v-for="(log, index) in logs" :class="{ red: aa }" :key="index" class="log-item">
        <card :text="(index + 1) + ' . ' + log"></card>
      </li>
    </ul>
  </div>
</template>

<script>
import { formatTime } from '@/utils/index'
import card from '@/components/card'

export default {
  components: {
    card
  },

  data () {
    return {
      arr: ["apple","banana","pear"],
      logs: [],
      indicatorcolor: "blue",
      indicatorDots: true,
      autoplay: true,
      interval: 2000,
      duration: 500,
      activecolor: "red",
      imgUrls: [
        {img: '/static/logs/1.jpg'},
        {img: '/static/logs/2.png'},
        {img: '/static/logs/3.jpg'}
      ]
    }
  },

  created () {
    let logs
    if (mpvuePlatform === 'my') {
      logs = mpvue.getStorageSync({key: 'logs'}).data || []
    } else {
      logs = mpvue.getStorageSync('logs') || []
    }
    this.logs = logs.map(log => formatTime(new Date(log)))
  }
}
</script>

<style>
swiper{
  width: 100%;
  height:150px;
}
.log-list {
  display: flex;
  flex-direction: column;
  padding: 40rpx;
}

.log-item {
  margin: 10rpx;
}
</style>
