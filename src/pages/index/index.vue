<template>
  <div>
    <div class="userinfo" @click="bindViewTap">
      <img class="userinfo-avatar" v-if="userInfo.avatarUrl" :src="userInfo.avatarUrl" background-size="cover"/>
      <div class="userinfo-nickname">
        <card :text="userInfo.nickName"></card>
      </div>
    </div>

    <van-cell-group>
      <van-cell value="内容" icon="shop" is-link>
        <view slot="title">
          <span class="van-cell-text">单元格</span>
          <van-tag type="danger">标签</van-tag>
        </view>
      </van-cell>
      <van-cell title="单元格" icon="location" is-link/>
      <van-cell title="单元格" @click="toLog">
        <van-icon slot="right-icon" name="search" class="van-cell__right-icon"/>
      </van-cell>
    </van-cell-group>
    <!--<div class="container" @click="clickHandle('test click', $event)">-->
    <van-card
      desc="描述信息"
      title="商品标题"
      :thumb="imageURL"
    />
    <button open-type="getUserInfo" @getuserinfo="bindGetUserInfo" @click="getUserInfo">获取权限</button>
    <!--<div class="usermotto">-->
    <!--<div class="user-motto">-->
    <!--<card :text="motto"></card>-->
    <!--</div>-->
    <!--</div>-->

    <!--<form class="form-container">-->
    <!--<input type="text" class="form-control" v-model="motto" placeholder="v-model" />-->
    <!--<input type="text" class="form-control" v-model.lazy="motto" placeholder="v-model.lazy" />-->
    <!--</form>-->
    <!--<a href="/pages/counter/main" class="counter">去往Vuex示例页面</a>-->
    <!--<van-tabbar fixed :active="active" @change="onChange">-->
    <!--<van-tabbar-item icon="shop">标签</van-tabbar-item>-->
    <!--<van-tabbar-item icon="chat" dot>标签</van-tabbar-item>-->
    <!--<van-tabbar-item icon="records" info="5">标签</van-tabbar-item>-->
    <!--<van-tabbar-item icon="gold-coin" info="20">标签</van-tabbar-item>-->
    <!--</van-tabbar>-->
  </div>
</template>

<script>
  import card from '@/components/card'

  export default {
    data() {
      return {
        motto: 'Hello World',
        userInfo: {},
        active: 0,
        show: true,
        imageURL: 'http://mpvue.com/assets/lifecycle.jpg'
      }
    },

    components: {
      card
    },
    mounted() {
      this.getSetting()
    },
    methods: {
      bindViewTap() {
        const url = '../logs/main'
        wx.navigateTo({url})
      },
      onClose() {
        this.setData({show: false})
      },
      onChange(event) {
        this.active = event.mp.detail
      },
      getSetting() {
        wx.getSetting({
          success: function (res) {
            if (res.authSetting['scope.userInfo']) {
              wx.getUserInfo({
                success: function (res) {
                  console.log(res.userInfo)
                  //用户已经授权过
                  console.log('用户已经授权过')
                }
              })
            } else {
              console.log('用户还未授权过')
            }
          }
        })
      },
      getUserInfo() {
        console.log('click事件首先触发')
        // 判断小程序的API，回调，参数，组件等是否在当前版本可用。  为false 提醒用户升级微信版本
        // console.log(wx.canIUse('button.open-type.getUserInfo'))
        if (wx.canIUse('button.open-type.getUserInfo')) {
          // 用户版本可用
        } else {
          console.log('请升级微信版本')
        }
      },
      bindGetUserInfo(e) {
        console.log(e.mp.detail.rawData)
        if (e.mp.detail.rawData) {
          console.log('用户按了允许授权按钮')
        } else {
          console.log('用户按了拒绝按钮')
        }
      },
      clickHandle(msg, ev) {
        console.log('clickHandle:', msg, ev)
      },
      toLog(item) {
        console.log(item)
        debugger
        var url = '../regist/regist'
        wx.navigateTo({url})
        // wx.switchTab({url})
      }
    },
    created() {
      // 调用应用实例的方法获取全局数据
      // this.getUserInfo()
    }
  }
</script>

<style scoped>
  .userinfo {
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  .userinfo-avatar {
    width: 128 rpx;
    height: 128 rpx;
    margin: 20 rpx;
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

  .counter {
    display: inline-block;
    margin: 10px auto;
    padding: 5px 10px;
    color: blue;
    border: 1px solid blue;
  }
</style>
