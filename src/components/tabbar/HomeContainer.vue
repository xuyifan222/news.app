<template>
    <div>
        <mt-swipe :auto="4000">
            <mt-swipe-item v-for="(item, index) in lunbolist" :key="index">
                <img :src="item.img">
            </mt-swipe-item>
        </mt-swipe>
		<ul class="mui-table-view mui-grid-view mui-grid-9">
		    <li class="mui-table-view-cell mui-media mui-col-xs-4 mui-col-sm-3"><router-link to="/home/newsList">
		        <img src="../../image/menu1.png" alt="">
		        <div class="mui-media-body">新闻资讯</div></router-link></li>
		    <li class="mui-table-view-cell mui-media mui-col-xs-4 mui-col-sm-3"><router-link to="/home/NewsPicture">
		        <img src="../../image/menu2.png" alt="">
		        <div class="mui-media-body">图片分享</div></router-link></li>
		    <li class="mui-table-view-cell mui-media mui-col-xs-4 mui-col-sm-3"><a href="#">
		        <img src="../../image/menu3.png" alt="">
		        <div class="mui-media-body">商品购买</div></a></li>
		    <li class="mui-table-view-cell mui-media mui-col-xs-4 mui-col-sm-3"><a href="#">
		        <img src="../../image/menu4.png" alt="">
		        <div class="mui-media-body">留言反馈</div></a></li>
		    <li class="mui-table-view-cell mui-media mui-col-xs-4 mui-col-sm-3"><a href="#">
		        <img src="../../image/menu5.png" alt="">		            
		        <div class="mui-media-body">视频专区</div></a></li>
		    <li class="mui-table-view-cell mui-media mui-col-xs-4 mui-col-sm-3"><a href="#">
		        <img src="../../image/menu6.png" alt="">
		        <div class="mui-media-body">联系我们</div></a></li>
		    </ul> 
    </div>    
</template>

<script>
import { Toast } from "mint-ui";
export default {
  data() {
    return {
      lunbolist: []
    };
  },
  created() {
    this.getLunbotu();
  },
  methods: {
    getLunbotu() {
      this.$http
        .get("api/getlunbo")
        .then(data => {
          if (data.body.status == 0) {
            this.lunbolist = data.body.message;
          } else {
            Toast("获取数据失败");
          }
        });
    }
  }
};
</script>

<style lang="scss" scoped>
.mint-swipe {
  height: 200px;

  .mint-swipe-item {
    &:nth-child(1) {
      background-color: red;
    }
    &:nth-child(2) {
      background-color: green;
    }
    &:nth-child(3) {
      background-color: violet;
    }
  }
  img {
    border: 0;
    height: 100%;
    width: 100%;
  }
}
.mui-grid-view.mui-grid-9 {
  background-color: white;
  border: none;
  img {
    width: 60px;
    height: 60px;
  }
  .mui-media-body {
    font-size: 13px;
  }
}
.mui-grid-view.mui-grid-9 .mui-table-view-cell {
  border: none;
}
</style>

