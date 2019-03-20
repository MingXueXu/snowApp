<template>
  <div class="container">
    <x-header :right-options="{showMore: true}" :left-options="{showBack: false}" @on-click-more="Login">我爱读书</x-header>
    <swiper loop auto :list="img_list" :index="img_index"></swiper>
    <grid :cols="4" :show-lr-borders="false">
      <grid-item :label="('Grid')" v-for="i in 8" :key="i">
        <img slot="icon" src="../assets/logo.png">
      </grid-item>
    </grid>
    <panel :header="'推荐'" :footer="footer" :list="list" :type="type"></panel>
    <tabbar>
      <tabbar-item>
        <img slot="icon" src="../assets/logo.png">
        <span slot="label">首页</span>
      </tabbar-item>
      <tabbar-item show-dot>
        <img slot="icon" src="../assets/logo.png">
        <span slot="label">书籍</span>
      </tabbar-item>
      <tabbar-item selected link="/Login">
        <img slot="icon" src="../assets/logo.png">
        <span slot="label">附近</span>
      </tabbar-item>
      <tabbar-item badge="2" link="/User">
        <img slot="icon" src="../assets/logo.png">
        <span slot="label">我的</span>
      </tabbar-item>
    </tabbar>
  </div>
</template>

<script>
import { Tabbar, TabbarItem, Group, Cell, XHeader, Grid, GridItem, Swiper, Panel } from 'vux'

const baseList = [{
  url: 'javascript:',
  img: 'https://ww1.sinaimg.cn/large/663d3650gy1fq66vvsr72j20p00gogo2.jpg',
  title: '送你一朵fua'
}, {
  url: 'javascript:',
  img: 'https://ww1.sinaimg.cn/large/663d3650gy1fq66vw1k2wj20p00goq7n.jpg',
  title: '送你一辆车'
}, {
  url: 'javascript:',
  img: 'https://ww1.sinaimg.cn/large/663d3650gy1fq66vw1k2wj20p00goq7n.jpg',
  title: '送你一次旅行',
  fallbackImg: 'https://ww1.sinaimg.cn/large/663d3650gy1fq66vw50iwj20ff0aaaci.jpg'
}]

const urlList = baseList.map((item, index) => ({
  url: 'http://m.baidu.com',
  img: item.img,
  fallbackImg: item.fallbackImg,
  title: `(可点击)${item.title}`
}))

export default {
  components: {
    Panel,
    XHeader,
    Tabbar,
    TabbarItem,
    Group,
    Cell,
    Grid,
    GridItem,
    Swiper
  },
   methods:{
     Login(){
         this.$router.push('/Login')
     }
  },
  created(){
        let _this=this
        this.$http.get('http://localhost:3000/api/news').then(({data}) => {
        var new_data = data.map((item, index) => ({
         src: item.src,
         fallbackSrc: item.src,
        title: item.title,
        desc: item.content
        }))
      _this.list = new_data
    })
  },
  data () {
    return {
      img_list: urlList,
      img_index: 0,
      msg: 'Hello World!',
      type: '1',
      list: [],
      footer: {
        title: '更多',
        url: 'http://vux.li'
      }
    }
  }
}
</script>

<style>
.container /deep/ .weui-tabbar {
  position: fixed;
}
</style>
