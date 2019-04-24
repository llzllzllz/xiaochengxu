<template>
  <div>
      <swiper :indicator-dots="indicatorDots"
      :autoplay="autoplay"
      :interval="interval"
      :duration="duration"
      style="height:200px">
        <block v-for="item in imgUrls" :key="item">
        <swiper-item>
          <image :src="item.img"/>
        </swiper-item>
        </block>
    </swiper>

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
      logs: [],
      indicatorDots: true,
      autoplay: true,
      interval: 2000,
      duration: 500,
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
.log-list {
  display: flex;
  flex-direction: column;
  padding: 40rpx;
}

.log-item {
  margin: 10rpx;
}
</style>
