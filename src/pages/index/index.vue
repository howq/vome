<template>
  <div>
    <div class="userinfo" @click="bindViewTap">
      <img class="userinfo-avatar" v-if="userInfo.avatarUrl" :src="userInfo.avatarUrl" background-size="cover" />
      <div class="userinfo-nickname">
        <card :text="userInfo.nickName"></card>
      </div>
    </div>

  <!--<div class="container" @click="clickHandle('test click', $event)">-->
    <van-card
      desc="描述信息"
      title="商品标题"
      :thumb="imageURL"
    />
    <van-card
      desc="描述信息"
      title="商品标题"
      :thumb="imageURL"
    />
    <van-card
      desc="描述信息"
      title="商品标题"
      :thumb="imageURL"
    />
    <van-card
      desc="描述信息"
      title="商品标题"
      :thumb="imageURL"
    />
    <van-card
      desc="描述信息"
      title="商品标题"
      :thumb="imageURL"
    />
    <van-card
      desc="描述信息"
      title="商品标题"
      :thumb="imageURL"
    />
    <van-card
      desc="描述信息"
      title="商品标题"
      :thumb="imageURL"
    />
    <van-card
      desc="描述信息"
      title="商品标题"
      :thumb="imageURL"
    />
    <van-card
      desc="描述信息"
      title="商品标题"
      :thumb="imageURL"
    />
    <van-card
      desc="描述信息"
      title="商品标题"
      :thumb="imageURL"
    />
    <van-card
      desc="描述信息"
      title="商品标题"
      :thumb="imageURL"
    />
    <van-card
      desc="描述信息"
      title="商品标题"
      :thumb="imageURL"
    />
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
  data () {
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

  methods: {
    bindViewTap () {
      const url = '../logs/main'
      wx.navigateTo({ url })
    },
    onClose () {
      this.setData({ show: false })
    },
    onChange (event) {
      this.active = event.mp.detail
    },
    getUserInfo () {
      // 调用登录接口
      wx.login({
        success: () => {
          wx.getUserInfo({
            success: (res) => {
              this.userInfo = res.userInfo
            }
          })
        }
      })
    },
    clickHandle (msg, ev) {
      console.log('clickHandle:', msg, ev)
    }
  },

  created () {
    // 调用应用实例的方法获取全局数据
    this.getUserInfo()
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

.counter {
  display: inline-block;
  margin: 10px auto;
  padding: 5px 10px;
  color: blue;
  border: 1px solid blue;
}
</style>
