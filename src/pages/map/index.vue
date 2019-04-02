<template>
  <div>
  <i-tabs :current="current_scroll" scroll @change="handleChangeScroll">
    <i-tab key="tab1" title="选项1"></i-tab>
    <i-tab key="tab2" title="选项2"></i-tab>
    <i-tab key="tab3" title="选项3"></i-tab>
    <i-tab key="tab4" title="选项4"></i-tab>
    <i-tab key="tab5" title="选项5"></i-tab>
    <i-tab key="tab6" title="选项6"></i-tab>
    <i-tab key="tab7" title="选项7"></i-tab>
    <i-tab key="tab8" title="选项8"></i-tab>
    <i-tab key="tab9" title="选项9"></i-tab>
  </i-tabs>
  </div>
</template>

<script>
import card from '@/components/card'

export default {
  components: {
    card
  },

  data () {
    return {
      current_scroll: 'tab1',
      motto: 'Hello miniprograme',
      userInfo: {
        nickName: 'mpvue',
        avatarUrl: 'http://mpvue.com/assets/logo.png'
      }
    }
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
    handleChange ({ detail }) {
      this.setData({
        current: detail.key
      })
    },
    handleChangeScroll (event) {
      this.current_scroll = event.mp.detail.key
    },
    clickHandle (ev) {
      console.log('clickHandle:', ev)
      // throw {message: 'custom test'}
    }
  },

  created () {
  }
}
</script>

<style>

</style>
