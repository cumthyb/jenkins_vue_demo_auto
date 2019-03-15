<template>
  <div id="app" @click="fireCD">
    <h1>点击下方看效果</h1>
    <div class="demo">
      <countDown 
        ref="countDown"
        :fire="fire"
        time="15"
        :tiping="tiping"
        :tipend="tipend"
        @onStatusChange="onStatusChange"
        @onEnd="onEnd"/>
     </div>
  </div>
</template>

<script>

import countDown from 'vue-canvas-countdown'
export default {
  name: 'App',
  components: {
    countDown
  },
  data () {
    return {
      fire: 0,
      tiping: {
        text: '倒计时进行中',
        color: '#fff'
      },
      tipend: {
        text: '倒计时结束',
        color: '#fff'
      }
    }
  },
  methods: {
    fireCD () {
      // 配置参数（更多配置如下表）
      this.tiping = {
        text: '请下注',
        color: '#fff'
      }
      this.tipend = {
        text: '停止下注',
        color: '#fff'
      }

      // 启动倒计时(效果如上图所示)      
      // 也支持：this.$refs.countDown.startCd()方式 启动倒计时
      this.fire++ 
    },
    onStatusChange (payload) {
      console.log('倒计时状态改变：', payload)
    },
    onEnd () {
      console.log('倒计时结束的回调函数')
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="less">

</style>
