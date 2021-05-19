<template>
  <div id="wrapper">
    <div id="scroller">
      <!-- head -->
      <div class="head" :class="{ signpb: height0 }">
        <img class="head-bg" src="@/assets/newImages/head-bg.png" alt="" />
        <div class="head-wrapper flex justify-between">
          <div>
            <img class="logo" src="@/assets/newImages/logo.png" alt="" />
          </div>

          <div class="text-container">
            <p>
              We are a global education company that aspires to be leaders in
              pioneering education for a sustainable future.
            </p>
            <p>
              At <strong>EiM</strong>, we want to empower our communities with
              the knowledge, skills and motivation to make a difference for
              people, society and the planet.
              <span
                v-show="height0"
                class="text-btn pointer"
                @click="
                  show = true;
                  height0 = false;
                "
                >READ MORE <img class="icon" src="@/assets/newImages/icon.png"
              /></span>
            </p>
            <span
              class="more-container"
              id="more-container"
              :class="{
                'animate__animated animate__fadeOut': !show,
                'animate__animated animate__fadeIn': show,
                hide: height0,
              }"
            >
              <p class="size-20">
                Given the social and environmental challenges facing our planet
                today, we know that as an education group we have a
                responsibility to be part of the solution.
              </p>
              <p class="size-20">
                That is why we are committed to investing in education brands
                with a strong focus on contributing to the sustainability and
                global citizenship agenda.
              </p>
              <p class="size-20">
                At the core of each of our brands is the common mission of
                pioneering Worldwise education solutions that are innovative,
                creative and world-changing. We hope to raise leaders who are
                passionate and equipped to create solutions to the world’s
                problems, both today and in the future.
              </p>
              <p class="size-20">
                With an agile leadership model and by leveraging synergies
                across our network, we are uniquely positioned to support and
                scale brands delivering pioneering education, so that more and
                more people are empowered to change the world.
                <span class="text-btn pointer size-18" @click="show = false"
                  >CLOSE<img
                    class="rotate icon"
                    src="@/assets/newImages/icon.png"
                /></span>
              </p>
            </span>

            <div class="text-right text-container">
              <span class="sign-wrapper">
                <img src="@/assets/newImages/sign2.png" style="width:196px;margin-bottom:10px;" alt="" />
                <div class="name-text">Fraser White</div>
                <div class="job-text">Founder, Chairman and CEO</div>
              </span>
              <span class="sign-wrapper">
                <img src="@/assets/newImages/sign1.png" style="width:196px;margin-bottom:10px;" alt="" />
                <div class="name-text">Karen Yung</div>
                <div class="job-text">Co-founder and CCO</div>
              </span>
            </div>
          </div>
        </div>
      </div>
      <img
        class="w-full bg-grey"
        src="@/assets/newImages/head-bot.png"
        alt=""
      />
      <!-- brand -->
      <div class="brand text-center bg-grey">
        <div class="color-grey size-40 brand-title">Our Brands</div>
        <div class="shcool-line school-row flex justify-between">
          <a class="school-item" href="https://www.dulwich.org/">
            <img class="brand-img" src="@/assets/newImages/brand1.png" alt="" />
          </a>
          <a class="school-item" href="https://www.dulwich.org/">
            <img class="brand-img" src="@/assets/newImages/brand2.png" alt="" />
          </a>
        </div>
        <div class="school-row flex justify-between m-b-114">
          <a class="school-item" href="https://www.dehong.cn/">
            <img class="brand-img" src="@/assets/newImages/brand3.png" alt="" />
          </a>
          <a class="school-item" href="https://www.wohui.io/">
            <img class="brand-img" src="@/assets/newImages/brand4.png" alt="" />
          </a>
        </div>
        <div class="school-row flex justify-between">
          <a class="school-item" href="https://eimventures.com/">
            <img class="brand-img" src="@/assets/newImages/brand5.png" alt="" />
          </a>
        </div>
      </div>
      <!-- footer -->
      <div class="footer">
        <div class="footer-wrapper flex justify-between align-center">
          <span class="color-white size-15">
            <a
              class="size-15 color-white"
              href="mailto:marianne.rehn@indulwich.com"
              >Contact Us</a
            ></span
          >
          <img class="logo-min" src="@/assets/newImages/logo.png" alt="" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import '@/assets/js/iscroll.js';
export default {
  name: 'App',
  data() {
    return {
      show: false,
      height0: true,
      myScroll: null,
    };
  },
  mounted() {
    document
      .getElementById('more-container')
      .addEventListener('animationend', (e) => {
        if (!this.show) {
          this.height0 = true;
        }
        setTimeout(() => {
          this.reloadScroll();
        }, 0);
      });
  },
  methods: {
    reloadScroll() {
      if (this.myScroll) {
        this.myScroll.destroy();
        this.myScroll = null;
      }
      this.myScroll = new IScroll('#wrapper', {
        mouseWheel: true,
        scrollbars: true,
        fadeScrollbars: true,
      });
    },
  },
};
</script>

<style>
body {
  overflow: hidden;
}
#wrapper {
  position: absolute;
  z-index: 1;
  top: 0;
  bottom: 0;
  left: 0;
  width: 100%;
  overflow: hidden;
}
#scroller {
  position: absolute;
  z-index: 1;
  -webkit-tap-highlight-color: rgba(0, 0, 0, 0);
  width: 100%;
  -webkit-transform: translateZ(0);
  -moz-transform: translateZ(0);
  -ms-transform: translateZ(0);
  -o-transform: translateZ(0);
  transform: translateZ(0);
  -webkit-touch-callout: none;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
  -webkit-text-size-adjust: none;
  -moz-text-size-adjust: none;
  -ms-text-size-adjust: none;
  -o-text-size-adjust: none;
  text-size-adjust: none;
}
/* common start */
.flex {
  display: flex;
}
.justify-between {
  justify-content: space-between;
}
.flex-1 {
  flex: 1;
}
.w-full {
  width: 100%;
}
.bg-grey {
  background: #fcfcfc;
}
.color-white {
  color: white;
}
.color-grey {
  color: #77777a;
}
.text-btn.size-18 {
  font-size: 18px;
}
.size-15 {
  font-size: 15px;
}
.size-20 {
  font-size: 20px;
}
.size-40 {
  font-size: 40px;
}

.text-center {
  text-align: center;
}
.text-right {
  text-align: right;
}
.align-center {
  align-items: center;
}
.pointer {
  cursor: pointer;
}
/* common end */
@font-face {
  font-family: 'DroidSerif';
  src: url('./assets/font/DroidSerif-Regular.ttf') format('truetype');
}
a {
  text-decoration: none;
}
* {
  padding: 0;
  margin: 0;
  font-family: 'DroidSerif';
  font-size: 0;
}
html {
  touch-action: none;
}
.head {
  padding-top: 130px;
  position: relative;
}
.head-bg {
  position: absolute;
  top: 0;
  z-index: -1;
  width: 100%;
  height: 100%;
  left: 0;
}
.text-container {
  max-width: 1094px;
}
p {
  font-size: 35px;
  font-weight: 400;
  line-height: 40px;
  color: #77777a;
  margin-bottom: 24px;
}
strong {
  font-size: 35px;
}
.logo {
  width: 298px;
  margin-right: 214px;
}
.head-wrapper {
  margin: 0 auto;
  max-width: 1606px;
}
.text-btn {
  font-size: 20px;
  font-weight: bold;
  line-height: 24px;
  color: #0c912f;
  text-decoration: underline;
  vertical-align: middle;
  margin-left: 5px;
}
.text-btn img {
  margin-left: 5px;
}
.brand {
  padding-bottom: 108px;
}
.brand-img {
  height: 347px;
}
.brand-title {
  padding: 88px 0;
}
.footer {
  height: 100px;
  line-height: 100px;
  background: #77777a;
}
.footer-wrapper {
  max-width: 2066px;
  padding: 0 140px;
  margin: 0 auto;
}
.logo-min {
  width: 80px;
  height: 74px;
  display: inline-block;
}
.sign-wrapper {
  width: 196px;
  text-align: center;
  display: inline-block;
}
.name-text {
  font-size: 20px;
  font-weight: 400;
  line-height: 15px;
  color: #77777a;
  margin-bottom: 5px;
}
.job-text {
  font-size: 13px;
  font-weight: 400;
  line-height: 15px;
  color: #77777a;
}
.school-item {
  transition: all 0.5s;
  cursor: pointer;
  display: inline-block;
  background: #fff;
}
.brand .shcool-line {
  margin-bottom: 114px;
}
.school-row {
  max-width: 1226px;
  margin: 0 auto;
}
.m-b-114{
  margin-bottom: 114px;
}
.school-item:hover {
  background: #dcdcdc54;
  border-radius: 5px;
}
.rotate {
  transform: rotate(180deg);
}
.more-container {
  overflow: hidden;
  display: inline-block;
  animation-duration: 0.4s;
}
.hide {
  height: 0;
}
.signpb {
  padding-bottom: 211px;
}
</style>
<style>
.school-item4 {
  border: solid 5px #fff;
  box-sizing: border-box;
}
@media screen and (max-width: 1606px) {
  .logo {
    width: 245px;
    margin-left: 150px;
  }
  .text-container {
    padding-right: 70px;
  }
  .head {
    padding-top: 80px;
  }
}
@media screen and (max-width: 1024px) {
  .logo {
    margin-left: 0;
  }
  .footer-wrapper {
    padding: 0 0 0 18px;
  }
  .logo-min {
    width: 68px;
    height: 63px;
    display: inline-block;
  }
  .school-row {
    width: 100%;
  }
  .school-item {
    width: 50%;
    box-shadow: 0px 1px 1px rgba(0, 0, 0, 0.16);
  }
  .school-item {
    margin-right: 5px;
    margin-bottom: 5px;
  }
  .brand-img {
    width: 100%;
    height: auto;
  }
  .size-40 {
    font-size: 25px;
  }
  .head-wrapper {
    flex-direction: column;
  }
  .logo {
    width: 139px;
    margin-bottom: 50px;
  }
  .head {
    padding: 50px 57px 0;
    width: 100%;
    box-sizing: border-box;
    padding-bottom: 112px;
  }
  p {
    font-size: 16px;
    line-height: 25px;
  }
  strong {
    font-size: 16px;
  }
  .size-15 {
    font-size: 12px;
  }
  .size-20 {
    font-size: 13px;
    line-height: 25px;
  }
  .text-btn.size-18 {
    font-size: 12px;
  }
  .text-btn {
    font-size: 12px;
    display: block;
    margin-left: 0;
  }
  .icon {
    width: 10px;
  }
  .brand .shcool-line {
    margin-bottom: 0;
  }
  .m-b-114{
    margin: 0;
  }
  .text-container {
    padding-right: 0;
  }
  .brand-title {
    padding: 40px 0 28px;
  }
  .brand {
    padding-bottom: 48px;
  }
  .footer {
    height: 63px;
    line-height: 63px;
  }
  .school-item4 {
    border: 0;
    box-sizing: border-box;
  }
  .name-text{
    font-size: 19px;
  }
  .job-text{
    font-size: 12px;
  }
}
.school-item {
  display: flex;
  align-items: center;
}
.brand4-img {
  width: 70%;
  height: auto;
  margin: 0 auto;
  transition: all 0.2s;
}
.school-item:hover .brand4-img {
  width: 75%;
}
</style>
