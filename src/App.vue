<template>
  <div>
    <v-header :seller="seller"></v-header>
    <div class="item">
       <router-link to="/" class="item-tab">商品</router-link>
       <router-link to="/seller" class="item-tab">商家</router-link>
       <router-link to="/ratings" class="item-tab">商家</router-link>
    </div>

    <router-view></router-view>

    <div>设置底部</div>
  </div>
</template>

<script type="text/ecmascript-6">
  import header from './components/header/header.vue';

  const ERR_OK = 0;
  export default {
    data() {
        return {
            seller: {}
        };
    },
    created() {
        this.$http.get('/api/seller').then((res) => {
            res = res.body;
            if (res.errno === ERR_OK) {
                this.seller = res.data;
                console.log(this.seller);
            }
        });
    },
    components: {
      'v-header': header
    }
  };
</script>

<style lang="stylus" rel="stylesheet/stylus">
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
  .item{
    display: flex;

  }
  .item a{
    flex: 1;
    text-align: center;
    height: 40px;
    line-height: 40px;
  }
</style>
