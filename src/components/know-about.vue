<script setup>
import { RouterLink, RouterView } from 'vue-router'

import { ref, onMounted, onUnmounted } from 'vue'

// 分开
const isActive = ref(false)

const toggleActive = () => {
  isActive.value = !isActive.value
}

onMounted(() => {
  const elements = document.querySelectorAll('.home-about-cate-wrap')
  elements.forEach((element) => {
    element.addEventListener('mouseenter', toggleActive)
    element.addEventListener('mouseleave', toggleActive)
  })
})

onUnmounted(() => {
  const elements = document.querySelectorAll('.home-about-cate-wrap')
  elements.forEach((element) => {
    element.removeEventListener('mouseenter', toggleActive)
    element.removeEventListener('mouseleave', toggleActive)
  })
})

const rotateSpan = (event) => {
  const element = event.currentTarget.querySelector('.home-about-cate-wrap')
  element.style.transform = 'rotateX(90deg)'
}

const resetSpan = (event) => {
  const element = event.currentTarget.querySelector('.home-about-cate-wrap')
  element.style.transform = 'none'
}
const handleMouseOver = (event) => {
  toggleActive()
  rotateSpan(event)
}
const handleMouseleft = (event) => {
  toggleActive()
  resetSpan(event)
}
</script>

<template>
  <div class="fp-page__wrap" style="margin-top: 70px;">
    <!-----轮播的选择---->
    <div class="home-about-cates">
      <div class="home-about-cates-wrap home-about-cates-wrap--active">
        <div class="home-about-cate">
          <div
            class="home-about-cate-wrap"
            @mouseover="handleMouseOver"
            @mouseleave="handleMouseleft"
            :class="{ 'home-about-cates-wrap--active': isActive }"
            style="transform: translateY(-0.6rem); transition-duration: 0ms"
          >
            <div class="span-wrapper">
              <div class="tab-dark">关于米哈游</div>
            </div>
          </div>
        </div>
      </div>
      <RouterLink to="/homehistory">
        <div class="home-about-cates-wrap">
          <div class="home-about-cate" >
            <div
              class="home-about-cate-wrap"
              @mouseover="handleMouseOver"
              @mouseleave="handleMouseleft"
              :class="{ 'home-about-cates-wrap--active': isActive }"
              style="transform: translateY(-0.6rem); transition-duration: 0ms"
            >
              <button class="custom-btn btn-12"><span>发展历程</span><span>发展历程</span></button>
            </div>
          </div>
        </div></RouterLink
      ><RouterView />
    </div>

    <!-- 内容 -->
    <div
      class="home-about-container"
      :class="{
        flag1: this.$route.meta.direction === 1,
        flag_1: this.$route.meta.direction === -1
      }"
      v-observe="'active'"
    >
      <div class="about-intro">
        <!-- 彩字部分 -->
        <div class="about-intro__vision">
          <div class="about-intro__vision-title">
            我们的愿景
            <b> Our Vision</b>
          </div>
          <div class="about-intro__vision-slg">
            <div class="anim">
              <p style="white-space: pre-wrap">2030年，打造出全球十亿人</p>
              <p style="white-space: pre-wrap; text-align: right">愿意生活在其中的虚拟世界。</p>
            </div>
          </div>
        </div>
        <!-- 关于米哈游 介绍部分 -->
        <div class="about-intro__mihoyo">
          <div class="about-intro__mihoyo-title">
            关于米哈游
            <b> About miHoYo</b>
          </div>
          <div class="about-intro__mihoyo-desc">
            <div>
              <p style="white-space: pre-wrap">
                米哈游成立于2011年，致力于为用户提供美好的、超出预期的产品与内容。米哈游陆续推出了多款高品质人气产品，包括《崩坏学园2》、《崩坏3》、《未定事件簿》、《原神》、《崩坏：星穹铁道》，动态桌面软件《人工桌面》以及社区产品《米游社》，并围绕原创IP打造了动画、音乐及周边等多元产品。即将上线的《绝区零》等同样受到全球玩家广泛关注。
              </p>
              <p style="white-space: pre-wrap">
                秉承着“<strong>技术宅拯救世界</strong>”的使命，米哈游始终致力于技术研发、探索前沿科技，在卡通渲染、人工智能、云游戏技术等领域积累了先进的技术能力。
              </p>
              <p style="white-space: pre-wrap">
                米哈游总部位于中国上海，并在新加坡、美国、加拿大、日本、韩国等国家和地区进行全球化布局。目前，公司员工5,000人，来自世界知名游戏/互联网/科技公司。
              </p>
              <p style="white-space: pre-wrap; min-height: 1.5em"></p>
              <p style="white-space: pre-wrap; min-height: 1.5em"></p>

              <!-- 底部 -->
              <p style="white-space: pre-wrap">
                <strong>米哈游的研发理念</strong>
              </p>
              <p style="white-space: pre-wrap">
                Something New | Something Exciting | Something Out of Imagination
              </p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
/* --------------------------------- */
/* 整体页面 */
/* --------------------------------- */
.home {
  position: relative;

  width: 100%;
  /* background-color: #f8f9fb; */
  height: 100%;
  font-family: 'Microsoft YaHei', 微软雅黑, 'MicrosoftJhengHei', PingFang, MingLiu, sans-serif;
}
.home-about {
  height: 100%;
  /* background-color: #f8f9fb; */
  width: 100%;
  overflow: hidden;
}
/* --------------------------------- */
/*左侧信息*/
/* --------------------------------- */
.aside-slogan[data-v-5dd2d15e] {
  position: absolute; /* 绝对定位 */
  left: 1rem;
  bottom: 7.38rem;
}
/* 左侧线部分 */
.aside-slogan__line[data-v-5dd2d15e] {
  position: absolute; /* 绝对定位 */
  top: -13rem;
  left: -0.2rem;
  width: 10rem;
  height: 20.28rem;
  background: url(./components/img/line.a3e37b6.png) no-repeat center center/100% 100%; /* 背景图片 */
}
.aside-slogan__text[data-v-5dd2d15e] {
  position: relative;
  top: 6rem;
  left: 2.2rem;
  z-index: 1;
  width: 0.4rem;
}
/* --------------------------------- */
/*右侧 aboutus*/
/* --------------------------------- */
.home-about-decoration {
  position: absolute;
  top: 0.9rem;
  right: 1rem;
  width: 10rem;
}
.home-about-decoration {
  -webkit-transition-delay: 2000ms;
  -o-transition-delay: 2000ms;
  transition-delay: 2000ms;
  -webkit-transition:
    opacity 1500ms,
    -webkit-transform 1500ms;
  transition:
    opacity 1500ms,
    -webkit-transform 1500ms;
  -o-transition:
    opacity 1500ms,
    transform 1500ms;
  transition:
    opacity 1500ms,
    transform 1500ms;
  transition:
    opacity 1500ms,
    transform 1500ms,
    -webkit-transform 1500ms;
}
/* --------------------------------- */
/* home-about-cates */
/* --------------------------------- */
.home-about-cates {
  display: -webkit-box; /* 采用flex布局 */
  display: -ms-flexbox;
  display: flex;
  -webkit-box-pack: end; /* 内容右对齐 */
  justify-content: flex-end;
  -webkit-box-align: center; /* 垂直居中对齐 */
  -ms-flex-align: center;
  align-items: center;
  margin-bottom: 10rem;
  margin-right: 2rem;
  top: 50px;
  right: 160px;
  position: relative;
}

.home-about-cates-wrap {
  /**应用于子元素，用于包装关于米哈游的内容 */
  position: relative;

  overflow: hidden; /**超出内容部分隐藏。 */
  margin-right: -1px;
  cursor: pointer; /*可以点击 */
}
.home-about-cate {
  height: 20px;
  width: 120px;
  overflow: hidden;
}

.home-about-cate .tab-dark {
  display: block;
  font-size: 0.9rem;
  height: 40px;
  width: 100px;
  line-height: 2.3rem;
  position: relative;
  padding: 0 2rem;
}
.home-about-cate span {
  display: block;
  font-size: 0.9rem;
  height: 40px;
  width: 100px;
  line-height: 1rem;
  position: relative;
  padding: 0 2rem;
}
/* 不点击的 */
.home-about-cate .tab-dark {
  color: #fff;
  background: #3778e5;
}

.btn-12 {
  position: relative;
  right: 15px;
  bottom: 10px;
  border: none;
  box-shadow: none;
  /* width: 10px; */
  height: 40px;
  line-height: 42px;
  -webkit-perspective: 230px;
  perspective: 230px;
  cursor: pointer;
}
.btn-12 span {
  background: #3778e5;
  background: linear-gradient(0deg, rgba#3778e5 0%, rgb(0, 172, 238, 1) 100%);
  display: block;
  position: absolute;

  width: 140px;
  height: 40px;

  border-radius: 0px;
  margin: 0;
  text-align: center;
  -webkit-box-sizing: border-box;
  -moz-box-sizing: border-box;
  box-sizing: border-box;
  -webkit-transition: all 0.3s;
  transition: all 0.3s;
}
/* 悬停时 */
.btn-12 span:nth-child(1) {
  color: #f8f9fb;
  -webkit-transform: rotateX(90deg);
  -moz-transform: rotateX(90deg);
  transform: rotateX(90deg);
  -webkit-transform-origin: 50% 50% -20px;
  -moz-transform-origin: 50% 50% -20px;
  transform-origin: 50% 50% -20px;
}
.btn-12 span:nth-child(2) {
  /* background-color: #fff; */
  background-color: #8394b50b;
  -webkit-transform: rotateX(0deg);
  -moz-transform: rotateX(0deg);
  transform: rotateX(0deg);
  -webkit-transform-origin: 50% 50% -20px;
  -moz-transform-origin: 50% 50% -20px;
  transform-origin: 50% 50% -20px;
}
.btn-12:hover span:nth-child(1) {
  -webkit-transform: rotateX(0deg);
  -moz-transform: rotateX(0deg);
  transform: rotateX(0deg);
}
.btn-12:hover span:nth-child(2) {
  color: transparent;
  -webkit-transform: rotateX(-90deg);
  -moz-transform: rotateX(-90deg);
  transform: rotateX(-90deg);
}
/* --------------------------------- */
/*内容*/
/* --------------------------------- */
.home-about-container {
  position: relative;
  width: 1000px;
  height: 800px;
  bottom: 90px;
  left: 100px;
}
.home-about-container > div {
  position: absolute;
  left: 50%;
  top: 0;
  -webkit-transform: translateX(-50%);
  -ms-transform: translateX(-50%);
  transform: translateX(-50%);
}

.about-intro {
  width: 98%;
  height: 100%;
  padding-left: 19rem;
}
.about-intro img {
  width: 100%;
}
.about-intro__vision {
  max-height: 400px;
}
/* 大小标题 */
.about-intro__vision-title,
.about-intro__mihoyo-title {
  position: relative;
  margin-bottom: 1rem;
  font-size: 1.3rem;
  font-weight: bold;
  color: #242933;
}
.about-intro__vision-title b,
.about-intro__mihoyo-title b {
  position: absolute;
  left: 6rem;
  bottom: -0.6rem;
  font-size: 0.5rem;
  font-weight: normal;
  color: #ccc;
  letter-spacing: 0.1em;
  font-family: HarmonyOS, Arial, Helvetica, sans-serif;
  text-transform: uppercase;
}

/**彩字设置 */

.about-intro__vision-slg {
  position: relative;
  display: inline-block;

  width: calc(100% - 15.76rem);
  padding-left: 3.2rem;
  width: 730px;
  margin-bottom: 1.4rem;
  margin-left: 3.64rem;
  font-size: 2.3rem;
  line-height: 2.3rem;
  letter-spacing: 0.1em;
  font-weight: lighter;
  color: #4ea1d9;
}
.about-intro__vision-slg.pureColor {
  background: none;
  pointer-events: none;
}
.about-intro__vision-slg.pureColor em {
  background: none;
  -webkit-background-clip: none;
}
.about-intro__vision-slg strong {
  color: #74d5ee;
  font-weight: inherit;
}
.about-intro__vision-slg em {
  color: #418ae0;
  font-style: normal;
  background-image: -o-linear-gradient(225deg, #dc8bc3 0, #418ae0 100%);
  background-image: linear-gradient(-135deg, #dc8bc3 0, #418ae0 100%);
  -webkit-text-fill-color: rgba(0, 0, 0, 0);
  -webkit-background-clip: text;
}
.about-intro__vision-slg u {
  color: #dc8bc3;
  text-decoration: none;
}
.about-intro__vision-slg::before,
.about-intro__vision-slg::after {
  content: '';
  position: absolute;
  width: 0.38rem;
  height: 1.25rem;
  background-repeat: 0;
  background-size: cover;
  background-position: center center;
}
.about-intro__vision-slg::before {
  left: 0;
  top: 0;
  background-image: url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAAgAAAAZCAYAAAAMhW+1AAAAAXNSR0IArs4c6QAAACZJREFUOE9j9Ft48z8DHsBIXQWb4tUZ0W1DsWJUASR4RsNhcIcDADoPYG82O/IpAAAAAElFTkSuQmCC);
}
.about-intro__vision-slg::after {
  right: 0;
  bottom: 0;
  background-image: url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAAgAAAAZCAYAAAAMhW+1AAAAAXNSR0IArs4c6QAAAChJREFUOE9jZMACrsx98h8mzDiqABwCo+EASQhDIxyQUzC2BMxIsQIAEOdTTmAeOPYAAAAASUVORK5CYII=);
}
.about-intro__vision-slg .anim {
  background-image: -o-linear-gradient(
    225deg,
    #418ae0,
    #56a0d8,
    #dc8bc3,
    #56a0d8,
    #418ae0,
    #56a0d8,
    #dc8bc3,
    #56a0d8,
    #418ae0
  );
  background-image: linear-gradient(
    -135deg,
    #418ae0,
    #56a0d8,
    #dc8bc3,
    #56a0d8,
    #418ae0,
    #56a0d8,
    #dc8bc3,
    #56a0d8,
    #418ae0
  );
  background-image: -ms-linear-gradient(
    -135deg,
    #418ae0,
    #56a0d8,
    #dc8bc3,
    #56a0d8,
    #418ae0,
    #56a0d8,
    #dc8bc3,
    #56a0d8,
    #418ae0
  );
  -webkit-text-fill-color: rgba(0, 0, 0, 0);
  -webkit-background-clip: text;
  background-size: 200% 100%;
  -webkit-animation: masked-animation 3s infinite linear;
  animation: masked-animation 3s infinite linear;
}
@-webkit-keyframes masked-animation {
  0% {
    background-position: 0 -100%;
  }
  100% {
    background-position: -100% 0;
  }
}
@keyframes masked-animation {
  0% {
    background-position: 0 -100%;
  }
  100% {
    background-position: -100% 0;
  }
}
.about-intro__mihoyo-desc {
  text-align: left;
  margin-bottom: 0.7rem;
  font-size: 0.8rem;
  color: #3d424d;
  line-height: 1.34rem;
  height: 2rem;
}
.about-intro__mihoyo-desc p {
  margin-bottom: 0.1rem;
}
.about-intro__mihoyo-desc strong {
  color: #3778e5;
  font-weight: bold;
}
/* --------------------------------- */
/* 背景 */
/* --------------------------------- */
.fp-page__wrap {
   /* 背景基础设置 */
   height: 100%;
  width: 100%;
  background-size: 100% 100%;
  position: fixed;
  /* left: -10px; */
  margin: 0;

  background:
	/* 水平条纹 */
    -webkit-linear-gradient(
      /*渐变方向:从上到下*/ top,
      /*最开始背景色*/ #8394b50b 0,
      /* 背景色 */ /* 这几行用于控制网格线条粗细 */ /*到3.5px均背景色*/ #8394b50b 3.5px,
      /*到4.3px过渡为浅蓝色线条色*/ #576e971c 4.1px,
      /* 线条色 */ /*以此类推*/ #8394b50b 4.7px,
      #8394b50b 60px,
      #4f689506 60px
    ),
    /* 垂直条纹 */ -webkit-linear-gradient(left, /*最开始背景色*/ #8394b50b 0, /*到3.5px均背景色*/
          #8394b50b 3.5px, /*到4.3px过渡为浅蓝色线条色*/ #576e971c 4.1px, /*以此类推*/ #8394b50b
          4.7px, #8394b50b 60px, #4f689506 60px);
  /* 网格大小参数 */
  -webkit-background-size: 20px 20px;
  -moz-background-size: 20px 20px;
  background-size: 20px 20px;
}
/* --------------------------------- */
/* 上下滚动延迟 */
/* --------------------------------- */
.flag {
  opacity: 0;
  filter: blur(5px);
  transition: all 1.5s;
  transform: translateY(-5%);
}
.flag1 {
  transition: ease-out 0.6s;
  transform: translateY(20%);
}
.flag_1 {
  transition: ease-out 0.6s;
  transform: translateY(-20%);
}
.flag2 {
  opacity: 0;
  filter: blur(5px);
  transition: all 1.5s;
  transform: translateY(5%);
}
.active {
  opacity: 1;
  filter: blur(0);
  transform: translateY(0);
}
</style>
