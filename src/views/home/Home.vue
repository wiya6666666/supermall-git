<template>
  <div id="home">
    <!-- 顶部 -->
    <nav-bar class="home_nav">
      <template v-slot:center>
        <div>购物街</div>
      </template>
    </nav-bar>
    <!-- 轮播图 -->
    <home-swiper :banners="banners"></home-swiper>
    <!-- 推荐页 -->
    <home-recommends :recommends="recommends"></home-recommends>
    <home-feature></home-feature>
  </div>
</template>

<script>
import NavBar from "@/components/common/navbar/NavBar";
import HomeSwiper from "./childComps/HomeSwiper";
import HomeRecommends from "./childComps/HomeRecommends";
import HomeFeature from "./childComps/HomeFeature";
import { getHomeMultiData } from "@/network/home";
export default {
  name: "home",
  components: {
    NavBar,
    HomeSwiper,
    HomeRecommends,
    HomeFeature,
  },
  data() {
    return {
      // result: null,
      banners: [],
      recommends: [],
    };
  },
  created() {
    getHomeMultiData().then((res) => {
      // console.log(res.data.recommend.list);
      // this.result = res;
      this.banners = res.data.banner.list;
      this.recommends = res.data.recommend.list;
    });
  },
  methods: {},
};
</script>

<style>
#home {
  padding-top: 44px;
}
.home_nav {
  background-color: var(--color-tint);
  color: #ffffff;
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 1;
}
</style>