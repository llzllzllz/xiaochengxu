<template>
  <div @click="clickHandle">
    <i-notice-bar v-if="show === true" icon="systemprompt" loop>
    {{year}}推文讲坛正式上线，望广大用户大力支持！
    </i-notice-bar>
    
    <i-grid i-class="no-border">
      <i-grid-item i-class="no-border" v-for="item in items" :key="item">
        {{item}}
      </i-grid-item>
    </i-grid>
  <i-grid i-class="no-border">
    <i-grid-item i-class="no-border">
        <i-grid-icon>
            <image src="/static/grid/1.png" />
        </i-grid-icon>
        <i-grid-label>科技</i-grid-label>
    </i-grid-item>
    <i-grid-item i-class="no-border">
        <i-grid-icon>
            <image src="/static/grid/2.png" />
        </i-grid-icon>
        <i-grid-label>法律</i-grid-label>
    </i-grid-item>
    <i-grid-item i-class="no-border">
        <i-grid-icon>
            <image src="/static/grid/3.png" />
        </i-grid-icon>
        <i-grid-label>自然</i-grid-label>
    </i-grid-item>
  </i-grid>
  <i-grid i-class="no-border">
    <i-grid-item i-class="no-border">
        <i-grid-icon>
            <image src="/static/grid/4.png" />
        </i-grid-icon>
        <i-grid-label>人性</i-grid-label>
    </i-grid-item>
    <i-grid-item i-class="no-border">
        <i-grid-icon>
            <image src="/static/grid/5.png" />
        </i-grid-icon>
        <i-grid-label>战略</i-grid-label>
    </i-grid-item>
    <i-grid-item i-class="no-border">
        <i-grid-icon>
            <image src="/static/grid/6.png" />
        </i-grid-icon>
        <i-grid-label>心理</i-grid-label>
    </i-grid-item>
 </i-grid>
 <i-panel title="论坛列表">
      <view i-class="top-padding">
      <i-card title="天涯科技论坛" extra="核心科技" i-class="top-padding" thumb="https://i.loli.net/2017/08/21/599a521472424.jpg">
        <view slot="content">令你眼花缭乱的技术</view>
        <view slot="footer">火星东部1-01</view>
      </i-card>
      <view i-class="top-padding"></view>
      <i-card title="识知法律论坛" i-class="top-padding" extra="最新法律修订" thumb="https://i.loli.net/2017/08/21/599a521472424.jpg">
        <view slot="content">更新及时</view>
        <view slot="footer">火星东部2-01</view>
      </i-card>
      <view i-class="top-padding"></view>
      <i-card title="自然科学讲坛" i-class="top-padding" extra="探索宇宙" thumb="https://i.loli.net/2017/08/21/599a521472424.jpg">
        <view slot="content">令人恍然大悟</view>
        <view slot="footer">火星西部1-01</view>
      </i-card>
      <view i-class="top-padding"></view>
      <i-card title="人性之美讲坛" i-class="top-padding" extra="揭露人性" thumb="https://i.loli.net/2017/08/21/599a521472424.jpg">
        <view slot="content">人性复杂而又简单</view>
        <view slot="footer">火星西部3-01</view>
      </i-card>
      <view i-class="top-padding"></view>
      <i-card title="战略决策讲坛" i-class="top-padding" extra="一个选择改变现在" thumb="https://i.loli.net/2017/08/21/599a521472424.jpg">
        <view slot="content">学有所得</view>
        <view slot="footer">火星北部4-01</view>
      </i-card>
      <view i-class="top-padding"></view>
      <i-card title="心理讲坛" i-class="top-padding" extra="形容你的现在" thumb="https://i.loli.net/2017/08/21/599a521472424.jpg">
        <view slot="content">爱上心理学</view>
        <view slot="footer">火星北部5-01</view>
      </i-card>
    </view>
    </i-panel>
  </div>
</template>

<script>
import card from '@/components/card'

export default {
  data () {
    return {
      show: false,
      year: '2019年4月3号',
      items: ['科技', '法律', '自然', '心理', '展览', '人性'],
      motto: 'Hello miniprograme',
      userInfo: {
        nickName: 'mpvue',
        avatarUrl: 'http://mpvue.com/assets/logo.png'
      }
    }
  },

  components: {
    card
  },

  methods: {
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
div >>> .no-border {
  border-width: 0pt;
}
div >>> .top-padding {
  padding-top:30pt;
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
</style>
