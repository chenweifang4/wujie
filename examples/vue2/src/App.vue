<template>
  <div id="app">
    <div id="nav" v-if="$route.name !== 'postmessage'">
      <router-link to="/home">首页</router-link> | <router-link to="/dialog">弹窗</router-link> |
      <router-link to="/location">路由</router-link> | <router-link to="/communication">通信</router-link>
    </div>
    <router-view />
  </div>
</template>

<script>
export default {
  watch: {
    // 在 vue2-sub 路由下主动告知主应用路由跳转，主应用也跳到相应路由高亮菜单栏
    $route() {
      window.$wujie?.bus.$emit("sub-route-change", "vue2", this.$route.path);
    },
  },
};
</script>
