<template>
  <div @click="clickHandle">
    <view>
      <view class="user">
        <view class="text1">用户名</view>
        <i-input :value="name" @change="changeName($event)"  autofocus placeholder="请输入用户名" maxlength="20" />
      </view>
      <view class="psd">
        <view class="text1">密码</view>  
        <i-input :value="password" password="true" @change="changePassword($event)"  placeholder="请输入密码" maxlength="30" />
        <i-button class="button1" @click="login" type="primary" size="default">登陆</i-button>
      </view>
    <view class="left">
      <text style="frontsize:25px">no number?</text><image style = "width:20px;height:20px" src="/static/grid/wechat.png"></image>
    </view>
    </view>
  </div>
</template>

<script>
import card from '@/components/card'

export default {
  data () {
    return {
      name:"",
      password:""
    }
  },

  components: {
    card
  },
  
  methods: {
     changeName (event) {
      this.name = event.mp.detail.detail.value
    },
    changePassword (event) {
      this.password = event.mp.detail.detail.value
    },
    login () {
      let that = this
      let url = '../mine/main'
      if (this.name && this.password) {
           mpvue.navigateTo({url})
        } else {
         that.name= this.name,
         that.password= this.name,
         wx.showToast({
          title: '用户名或密码为空',
          icon: 'none',
          duration: 2000
        })
           }
        }
  },

  created () {
  }
}
</script>

<style scoped>
.button1{
  font-size: 25px;
  margin-top: 50rpx;
}
.text1{
  margin-left: 4%;
  font-size: 18px;
}
.user{
  margin-top: 50rpx;
  
}
.psd{
  margin-top: 50rpx;
}
div >>> .no-border {
  border-width: 0pt;
  color:chartreuse;
}
div >>> .top-padding {
  padding-top:10pt;
}
.userinfo {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.userinfo-avatar {
  width: 128rpx;
  height: 128rpx;
  margin: 20rpx;
  border-radius: 50%;
}

.userinfo-nickname {
  color: #aaa;
}

.usermotto {
  margin-top: 150px;
}

.form-control {
  display: block;
  padding: 0 12px;
  margin-bottom: 5px;
  border: 1px solid #ccc;
}
.all{
  width:7.5rem;
  height:1rem;
  background-color:blue;
}
.all:after{
  display:block;
  content:'';
  clear:both;
}
.left{
  float:left;
  width:3rem;
  height:1rem;
  background-color:red;
}

.right{
  float:left;
  width:4.5rem;
  height:1rem;
  background-color:green;
}

.nav-hover{
  color:red;
}

.nav-default{
  color: #aaa
}
.left{
  
}
</style>
