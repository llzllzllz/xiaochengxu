<template>
  <div @click="clickHandle">
    <i-notice-bar color="#5cadff" v-if="show === false" icon="systemprompt" closable loop>
    {{year}}推文讲坛正式上线，望广大用户大力支持！
    </i-notice-bar>
    
    <i-grid i-class="no-border">
      <i-grid-item i-class="no-border" v-for="item in items" :key="item">
        {{item}}
      </i-grid-item>
    </i-grid>

  <i-grid i-class="no-border">
    <i-grid-item i-class="no-border" v-for="item in images1" :key="item" @click="goList(item.url)">
        <i-grid-icon>
            <image :src="item.add" />
        </i-grid-icon>
        <i-grid-label>{{item.type}}</i-grid-label>
    </i-grid-item>
  </i-grid>
  <i-grid i-class="no-border">
     <i-grid-item i-class="no-border" v-for="item in images2" :key="item" @click="goList(item.url)">
        <i-grid-icon>
            <image :src="item.add" />
        </i-grid-icon>
        <i-grid-label>{{item.type}}</i-grid-label>
     </i-grid-item>
  </i-grid>
 <navigator url='/pages/count/main' open-type="navigate" hover-class='nav-hover' class='nav-default'>
  <i-button type="info" long="true">签到学习</i-button>
 </navigator>
 <i-panel title="论坛列表">
      <view i-class="top-padding" v-for="item in shops" :key="item">
      <i-card :title="item.name" :extra="item.introduction" i-class="top-padding" :thumb="item.image" full>
        <view slot="content">{{item.type}}</view>
        <view slot="footer">{{item.address}}</view>
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
      shops: [],
      show: false,
      year: '2019年4月3号',
      images1: [
      {add: '/static/grid/1.png',type:'科技', url:'../content/main?type=1'},
      {add: '/static/grid/2.png',type:'法律', url:'../content/main?type=2'},
      {add: '/static/grid/3.png',type:'自然', url:'../content/main?type=3'},
      ],
      images2: [
        {add: '/static/grid/4.png',type:'心理',url:'../content/main?type=4'},
        {add: '/static/grid/5.png',type:'环境',url:'../content/main?type=5'},
        {add: '/static/grid/6.png',type:'人性',url:'../content/main?type=6'}
      ],
      items: ['科技', '法律', '自然', '心理', '环境', '人性']
    }
  },

  components: {
    card
  },
  
  methods: {
     goList (url) {
      mpvue.navigateTo({ url })
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
    this.$http.get('http://s24.027365.net/', '').then((res)=>{
        console.log('res', res)
      }).catch(err=>{
    })
    const db = wx.cloud.database({ env: 'llz-a9aaae' })
    db.collection('shop').get().then(
      res => {
        this.shops = res.data
      }
    )
    //  cloud function
    wx.cloud.callFunction({ name: 'llz' }).then(
      res => {
        console.log(res)
      }
    )
  }
}
</script>

<style scoped>
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
</style>
