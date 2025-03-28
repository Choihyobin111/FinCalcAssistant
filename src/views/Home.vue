<template>
  <div :class="`${isDark ? 'slogan-dark-theme' : 'slogan-light-theme'} main`">
    <n-carousel autoplay show-arrow trigger="hover" style="margin-top:80px">
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
    <!-- <div class="title" >--欢迎使用SUFE金融计算助手！--</div>
    <div class="title" >--本工具旨在帮助您对金融理财与货币计算--</div>
    <div class="title" >--点击“功能大全” 开始使用吧！--</div> -->
   
 <!-- 功能一览 -->
 <div class = "interval">
      <div class="title" style="font-size:26px;font-weight:5px">功能一览</div>
    </div>
    <div ref="info4" :class="`${isDark ? 'functionlist-darktheme' : 'functionlist-lighttheme'}`">
      <n-card embedded title="投资/贷款计算">
        <template #cover>
          <n-icon :component="HandHoldingUsd" :size="150" class="tab-icon"/>
        </template>
      </n-card>
      <n-card embedded title="现金流计算">
        <template #cover>
          <n-icon :component="ChartMultiple24Filled" :size="150" class="tab-icon"/>
        </template>
      </n-card>
      <n-card embedded title="储蓄计算">
        <template #cover>
          <n-icon :component="Coins" :size="150" class="tab-icon"/>
        </template>
      </n-card>
      <n-card embedded title="汇率转化">
        <template #cover>
          <n-icon :component="Bitcoin" :size="150" class="tab-icon"/>
        </template>
      </n-card>
      <n-card embedded title="个税计算">
        <template #cover>
          <n-icon :component="BuildingGovernment24Filled" :size="150" class="tab-icon"/>
        </template>
      </n-card>
    </div>



    <div :class="`${isDark ? 'aboutus-darktheme' : 'aboutus-lighttheme'}`">
      <div class = "interval">
        <div class="title" style="font-size:26px;font-weight:5px">关于我们</div>
      </div>

      <div class="aboutus-item" ref="info1">
          <img ref="image" src="@/assets/pictures/Franctoryer.png" class="avatar">
          <n-space  vertical>
          <div class="slogan-text" style="margin-left:200px;margin-top:50px">Franctoryer-朱力涛</div>
          <div class="slogan-sidetext" style="margin-left:300px">SUFE CS专业22级在读</div>
        </n-space>
      </div>
      <div class="interval2"></div>
      <div class="aboutus-item" ref="info2" style="margin-left:500px">
          <n-space  vertical>
          <div class="slogan-text" style="margin-top:50px">Choihyobin-陈雨乐</div>
          <div class="slogan-sidetext">SUFE CS专业22级在读</div>
        </n-space>
        <img ref="image" src="@/assets/pictures/Choihyobin.png" class="avatar">
      </div>
      <div class="interval2"></div>
      <div class="aboutus-item" ref="info3">
          <img ref="image" src="@/assets/pictures/738NGX.png" class="avatar">
          <n-space  vertical>
          <div class="slogan-text" style="margin-left:200px;margin-top:50px">738NGX-吉宁岳</div>
          <div class="slogan-sidetext" style="margin-left:200px">SUFE CS专业22级在读</div>
        </n-space>
      </div>
    </div>

   

    <div style="height:50px;width:100%"></div>
    <div :class="`${isDark ? 'footer-darktheme' : 'footer-lighttheme'}`">
      <img ref="image" src="@/assets/pictures/keaidinie.jpg" class="avatar" style="height:100%;width:auto"> 喜欢本站的话可以喜欢一下或者投币支持哦！ </div>

  </div>
</template>

<script setup lang="ts">
import { ref, onMounted } from 'vue';
import { storeToRefs } from 'pinia';
import { useThemeStore } from '@/stores/themeStore';
import { gsap } from 'gsap';
import { NSpace, NCarousel, NCard, NAvatar, NIcon } from 'naive-ui';
import { ChartMultiple24Filled, BuildingGovernment24Filled } from "@vicons/fluent"
import { Coins, Bitcoin, HandHoldingUsd } from "@vicons/fa"


const { themeClass, isDark } = storeToRefs(useThemeStore());
const slogan = ref(null);
const info1 = ref(null);
const info2 = ref(null);
const info3 = ref(null);
const info4 = ref(null);
const info4unshowed = ref(true)

onMounted(() => {
  const observer = new IntersectionObserver(
    (entries) => {
      entries.forEach((entry) => {
        if (entry.isIntersecting) {
          // 元素进入视口时触发动画
          if (entry.target === info1.value) onInfoLoad1();
          if (entry.target === info2.value) onInfoLoad2();
          if (entry.target === info3.value) onInfoLoad3();
        } else {
          // 元素离开视口时重置状态
          resetInfo(entry.target);
        }
      });
    },
    { threshold: 0.1 }
  );
  const observer2 = new IntersectionObserver(
    (entries) => {
      entries.forEach((entry) => {
        if (entry.isIntersecting) {
          if (entry.target === info4.value && info4unshowed.value){ 
            onInfoLoad4()
            info4unshowed.value = false;  
          };
        }
      });
    },
    { threshold: 0.3 }
  );

  // 绑定观察器到所有元素
  if (info1.value) observer.observe(info1.value);
  if (info2.value) observer.observe(info2.value);
  if (info3.value) observer.observe(info3.value);
  if (info4.value) observer2.observe(info4.value);
});

const resetInfo = (target : any) => {
  gsap.set(target, { opacity: 0, x: target === info2.value ? 100 : -100 }); // 重置到初始状态
};
const onImageLoad = () => {
  gsap.fromTo(
    slogan.value, 
    { opacity: 0,x:100, y: 0 }, // 初始状态
    { opacity: 1,x:0, y: 0, duration: 1.5, ease: 'power2.out' } // 目标状态
  );
};
const onInfoLoad1 = () => {
  gsap.fromTo(
    info1.value,
    { opacity: 0,x:-50, y: 0 }, // 初始状态
    { opacity: 1,x:0, y: 0, duration: 3, ease: 'power2.out' } // 目标状态
  );
};
const onInfoLoad2 = () => {
  gsap.fromTo(
    info2.value,
    { opacity: 0,x:50, y: 0 }, // 初始状态
    { opacity: 1,x:0, y: 0, duration: 2, ease: 'power2.out' } // 目标状态
  );
};
const onInfoLoad3 = () => {
  gsap.fromTo(
    info3.value,
    { opacity: 0,x:-50, y: 0 }, // 初始状态
    { opacity: 1,x:0, y: 0, duration: 1.5, ease: 'power2.out' } // 目标状态
  )
};
const onInfoLoad4 = () => {
  gsap.fromTo(
    info4.value,
    { opacity: 0,x:0, y: 50 }, // 初始状态
    { opacity: 1,x:0, y: 0, duration: 1, ease: 'power2.out' } // 目标状态
  )
}
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
  background-color: rgb(188, 207, 250);
  width:100%;
  display:flex;
  align-items: center;
  justify-content:center;
}
.interval2{
  height:2px;
  background-color: rgb(161, 187, 222);
  width:100%;
  display:flex;
  align-items: center;
  justify-content:center;
}
.title{
  align-items: center;
  white-space: nowrap;
  font-size:20px;
  position:relative;
}
.aboutus-lighttheme, .aboutus-darktheme{
  height:auto;
  width:80%;
  display:flex;
  align-items: center;
  flex-direction: column;
  
}
.aboutus-lighttheme{
  background-color: rgb(251, 251, 251);
}
.aboutus-darktheme{
  background-color: rgb(35, 38, 39);
}
.aboutus-item{
  /* background-color: rgb(109, 180, 191); */
  width:100%;
  height:250px;
  display:flex;
  align-items: center;
  flex-direction: row;
}
.avatar{
  width:200px;
  margin:30px;
  margin-left:100px
}
.functionlist-lighttheme, .functionlist-darktheme{
  display:flex;
  flex-wrap: wrap;
  margin-left:2.5%;
  width:95%;
  margin-top:0%;
  margin-bottom:2.5%;
  justify-content: space-around;
  padding:50px;
}
.functionlist-lighttheme{
  background-color:aliceblue
}
.n-card{
  max-width:300px;
  margin:20px;
}
.tab-icon{
 margin-top:20px
}
.footer-lighttheme, .footer-darktheme{
  height:150px;
  width:100%;
  display:flex;
  align-items:center;
  justify-content: center;
  font-size:30px;
}
.footer-lighttheme{
  background-color: rgb(80, 106, 171);
  color:whitesmoke
}
.footer-darktheme{
  background-color: rgb(19, 35, 76);
  color:whitesmoke
}
</style>
