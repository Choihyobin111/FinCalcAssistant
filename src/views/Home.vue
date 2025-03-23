<template>
  <div :class="`${isDark ? 'slogan-dark-theme' : 'slogan-light-theme'} main`">
    <n-carousel autoplay  show-arrows style="margin-top:80px">
      <img
        class="carousel-img"
        src="@/assets/pictures/carousel1.png"
      >
      <img
        class="carousel-img"
        src="@/assets/pictures/carousel2.png"
      >
      <img
        class="carousel-img"
        src="@/assets/pictures/carousel3.png"
      >
      <img
        class="carousel-img"
        src="@/assets/pictures/carousel4.png"
      >
      <img
        class="carousel-img"
        src="@/assets/pictures/carousel5.png"
      >
    </n-carousel>


    <div style = "display: flex;flex-direction:row;align-items: center; margin:15px">
      <img ref="image" src="@/assets/pictures/FinAssistant.png" alt="Growth Image" class="growth-image" @load="onImageLoad"/>
      <div ref="slogan">
        <n-space vertical>
          <div class="slogan-text">一键计算，财富增长</div>
          <div class="slogan-sidetext">SUFE金融计算助手</div>
        </n-space>
      </div>
    </div>
    <div class="title" >--欢迎使用SUFE金融计算助手！--</div>
    <div class="title" >--本工具旨在帮助您对金融理财与货币计算--</div>
    <div class="title" >--点击“功能大全” 开始使用吧！--</div>
    <div class = "interval">
      <div class="title" style="font-size:26px;font-weight:5px;">--关于我们--</div>
    </div>


    <div :class="`${isDark ? 'aboutus-darktheme' : 'aboutus-lighttheme'}`">


      <div class="aboutus-item">
          <img ref="image" src="@/assets/pictures/Franctoryer.png" class="avatar">
          <n-space  vertical>
          <div class="slogan-text" style="margin-left:300px;margin-top:50px">Franctoryer-朱力涛</div>
          <div class="slogan-sidetext" style="margin-left:300px">SUFE CS专业22级在读</div>
        </n-space>
      </div>
      <div class="interval2"></div>
      <div class="aboutus-item">
          <n-space  vertical>
          <div class="slogan-text" style="margin-left:300px;margin-top:50px">Choihyobin-陈雨乐</div>
          <div class="slogan-sidetext" style="margin-left:300px">SUFE CS专业22级在读</div>
        </n-space>
        <img ref="image" src="@/assets/pictures/Choihyobin.png" class="avatar">
      </div>
      <div class="interval2"></div>
      <div class="aboutus-item">
          <img ref="image" src="@/assets/pictures/738NGX.png" class="avatar">
          <n-space  vertical>
          <div class="slogan-text" style="margin-left:300px;margin-top:50px">738NGX-吉宁岳</div>
          <div class="slogan-sidetext" style="margin-left:300px">SUFE CS专业22级在读</div>
        </n-space>
      </div>
    </div>

    <div style="height:50px;width:100%"></div>
    <div class="footer">
      <img ref="image" src="@/assets/pictures/keaidinie.jpg" class="avatar" style="height:100%;width:auto">-- 喜欢本网站的话可以喜欢一下或者投币支持哦！ --</div>

  </div>
</template>

<script setup lang="ts">
import { ref, onMounted } from 'vue';
import { storeToRefs } from 'pinia';
import { useThemeStore } from '@/stores/themeStore';
import { gsap } from 'gsap';
import { NSpace, NCarousel, NCard, NAvatar } from 'naive-ui';


const { themeClass, isDark } = storeToRefs(useThemeStore());
const slogan = ref(null);

const onImageLoad = () => {
  gsap.fromTo(
    slogan.value, 
    { opacity: 0,x:100, y: 0 }, // 初始状态
    { opacity: 1,x:0, y: 0, duration: 1, ease: 'power2.out' } // 目标状态
  );
};
</script>

<style scoped>

.slogan-light-theme, .slogan-dark-theme {
  width: 100%;
  text-align: center;
  font-weight: bold;
  margin-top:-1vh;
  /* margin-top: 20vh; */
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

/* 使图片适应页面 */
.growth-image {
  max-height: auto;  /* 你可以根据需要调整这个值 */
  max-width: 50vw;   /* 自适应页面宽度 */
  height: auto;
  margin-right: 15px; /* 与文字之间留一些间距 */
  transform: translateX(-5vw) translateY(-3vw); 

}

/* slogan 文字不换行并且自适应页面 */
.slogan-text {
  font-size: 3vw;  /* 根据页面宽度自适应大小 */
  white-space: nowrap;  /* 防止换行 */
  transform: translateX(-10vw) translateY(-3vw); /* 向左移动10vw */
  margin-left: 100px;
  padding-left: 100px;
}
.slogan-sidetext {
  font-size: 1.5vw;  /* 根据页面宽度自适应大小 */
  white-space: nowrap;  /* 防止换行 */
  transform: translateX(-10vw) translateY(-3vw); /* 向左移动10vw */
  margin-left: 100px;
  padding-left: 100px;
}

.slogan-dark-theme {
  color: aliceblue;
}

.main {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}
.carousel-img{
  width:100%;
  max-height:60vh;

}
.interval{
  height:8vh;
  background-color: rgb(127, 146, 189);
  width:100%;
  display:flex;
  align-items: center;
  justify-content:center;
}
.interval2{
  height:2px;
  background-color: rgb(88, 171, 180);
  width:100%;
  display:flex;
  align-items: center;
  justify-content:center;
}
.title{
  align-items: center;
  white-space: nowrap;
  font-size:20px;
}
.aboutus-lighttheme .aboutus-darktheme{
  height:auto;
  width:100%;
  display:flex;
  align-items: center;
  flex-direction: column;
}
.aboutus-lighttheme{
  background-color: rgb(240, 245, 249);
}
.aboutus-darktheme{
  background-color: rgb(35, 38, 39);
}
.aboutus-item{
  /* background-color: rgb(109, 180, 191); */
  width:100%;
  height:300px;
  display:flex;
  align-items: center;
  flex-direction: row;
}
.avatar{
  width:250px;
  margin:30px;
  margin-left:100px
}
.footer{
  height:150px;
  width:100%;
  background-color: rgb(127, 146, 189);
  display:flex;
  align-items:center;
  justify-content: center;
  font-size:30px;
}
</style>
