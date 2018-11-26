<template>
  <div id="app">
<v-toolbar dark tabs color="primary" :fixed="true">
    <!-- <v-toolbar-side-icon></v-toolbar-side-icon> -->
    <v-toolbar-title @click="index=false,$router.push('/')"><v-icon>language</v-icon>达伊神奇宝贝1.12.2服</v-toolbar-title>
    <v-spacer></v-spacer>
    <v-toolbar-items class="hidden-sm-and-down">


      <v-btn flat tag="a" href="https://pan.baidu.com/s/18oNBi1WHcJ-DkEOaRsC1jw" target="_blank">
        <v-icon>cloud_download</v-icon> 下载客户端
        </v-btn>
      <v-btn flat tag="a" id='qun' href="//shang.qq.com/wpa/qunwpa?idkey=2dfd24885cd52f883d76c20821865b4fe6c0f85f24b8bd3cabd2904389caa7af" target="_blank">
        <v-icon>link</v-icon> 加入服务器群
        </v-btn>
      <v-btn flat @click="page=0,$router.push('/list')">
      <v-icon>monetization_on</v-icon> 赞助表
        </v-btn>
      <v-btn flat>
      <v-icon>error_outline</v-icon> 关于</v-btn>
    </v-toolbar-items>

<v-tabs v-if="$route.path === '/list'"
        slot="extension"
        centered
        v-model="page"
        color="primary"
        slider-color="yellow"
      >
        <v-tab
          v-for="i in list"
          :key="i"
        >
           {{ i }}
        </v-tab>
      </v-tabs>

  </v-toolbar>
  <div class="main">
    <router-view ref="view"/>

    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  watch: {
    page: function(n, o) {
      if (this.$refs.view.toPage) this.$refs.view.toPage(n);
    }
  },
  data() {
    return {
      index: false,
      page: 0,
      list: ["传说中的宝可梦", "权限", "称号", "其他"]
    };
  }
};
</script>

<style>
.primary {
  background-color: #1867c0 !important;
  border-color: #1867c0 !important;
}
.v-icon {
  margin-right: 5px;
}
.v-toolbar__title .v-icon {
  margin-bottom: 2px;
}
#app {
  padding-top: 64px;
  padding-bottom: 64px;
}
.index-title {
  font-size: 20px;
  text-align: center;
  line-height: 64px;
  height: 64px;
}
.v-toolbar__title,
.v-tabs__div {
  cursor: pointer;
}
</style>
