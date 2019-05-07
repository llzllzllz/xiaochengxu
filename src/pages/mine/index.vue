<template>
  <div @click="clickHandle">
  <view class="userinfo">
    <view class="userinfo-avatar">
    <open-data type="userAvatarUrl"></open-data>
    </view>
    <open-data type="userNickName"></open-data>
  </view>
  <i-cell-group>
    <i-cell title="我的收藏" is-link url="/pages/logs/main"></i-cell>
    <i-cell title="接收通知">
    <switch slot="footer" checked />
    </i-cell>
  </i-cell-group> 
  <i-panel title="发布最新论点">
      <i-input :value="name" @change="changeName($event)" title="类名" autofocus placeholder="请输入" maxlength="20" />
      <i-input :value="address" @change="changeAddress($event)" title="主题" placeholder="请输入" maxlength="30" />
      <i-input :value="reason" @change="changeReason($event)" title="内容" placeholder="请输入" maxlength="50" />
      <i-input :value="link" @change="changeLink($event)" title="分享链接" placeholder="请输入" maxlength="100" />
  </i-panel>
  <i-button @click="handleClick" type="warning" size="default">发布</i-button>
  </div>
</template>

<script>
import card from '@/components/card'

export default {
  data () {
    return {
      name:"",
      address:"",
      reason:"",
      link:""
    }
  },

  components: {
    card
  },

  methods: {
    changeName (event) {
      this.name = event.mp.detail.detail.value
    },
    changeReason (event) {
      this.reason = event.mp.detail.detail.value
    },
    changeAddress (event) {
      this.address = event.mp.detail.detail.value
    },
    changeLink (event) {
      this.address = event.mp.detail.detail.value
    },
    handleClick () {
    if (this.name && this.reason && this.address) {
        wx.showToast({
          title: '发布了' + this.name + this.link,
          icon: 'success',
          duration: 2000
        })
        // TODO:将推荐数据提交到云数据库
      } else {
        wx.showToast({
          title: '信息不完整',
          icon: 'none',
          duration: 2000
        })
      }
    },
    bindViewTap () {
      const url = '../logs/main'
      if (mpvuePlatform === 'wx') {
        mpvue.switchTab({ url })
      } else {
        mpvue.navigateTo({ url })
      }
    },
    clickHandle (ev) {
      console.log('clickHandle:', ev)
      // throw {message: 'custom test'}
    }
  },

  created () {
    // let app = getApp()
  }
}
</script>

<style scoped>
.userinfo {
position: relative;
width: 750rpx;
height: 320rpx;
color: #666;
display: flex;
flex-direction: column;
align-items: center;
}
 
.userinfo-avatar {
overflow:hidden;
display: block;
width: 160rpx;
height: 160rpx;
margin: 20rpx;
margin-top: 50rpx;
border-radius: 50%;
border: 2px solid #fff;
box-shadow: 3px 3px 10px rgba(0, 0, 0, 0.2);
}
</style>
