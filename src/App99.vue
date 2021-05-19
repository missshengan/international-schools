<template>
  <div>
    <div class="logo-wrap">
      <div class="logo-wrap2">
        <img class="logo "
             src="@/assets/images/logo.png" />
      </div>
      <div class="gradient"></div>
    </div>
    <div id="wrapper">
      <div id="scroller">
        <div class="wrap">

          <div class="content">
            <div class="color-grey mb-30 size-28">
              We aspire to be the leaders in global education and sustainability.
            </div>
            <div class="width-812 mb-49  bold content-text"
                 id="content"
                 :class="{'scrollup':!showFull}">
              <div class="size-18 line-30">
                At EiM, we want to empower our communities with the knowledge, skills and motivation to make a difference for people, society and the planet.
                <span :class="{'hide':hideFullText}">
                  <span class="size-18 line-30 p">Given the social and environmental challenges facing our planet today, we know that as an education group we have a responsibility to be part of the solution. </span>
                  <span class="size-18 line-30 p">That is why we are committed to investing in education brands with a strong focus on contributing to the sustainability and global citizenship agenda.</span>
                  <span class="size-18 line-30 p"
                        style="margin-bottom:18rem;">At the core of each of our brands is the common mission of pioneering Worldwise education solutions that are innovative, creative and world-changing. We hope to raise leaders who are passionate and equipped to create solutions to the world’s problems, both today and in the future. </span>
                  <span class="size-18 line-30">With an agile leadership model and by leveraging synergies across our network, we are uniquely positioned to support and scale brands delivering pioneering education, so that more and more people are empowered to change the world. </span>
                </span>
                <span v-if="!showFull"
                      class="color-green size-18 cursor-pointer full-btn"
                      @click="scrollDown"> READ MORE &gt;</span>
                <span v-else
                      class="color-green size-18 cursor-pointer full-btn"
                      @click="scrollUp"> &lt; CLOSE</span>
              </div>

            </div>
            <div class="sign">
              <img class="mb-20"
                   src="@/assets/images/sign.png">
              <div class="mb-66 size-18 bold"> Fraser White, Founder and CEO</div>
            </div>
          </div>
          <div class="schools">
            <div class="color-grey mb-33 size-28">Our schools</div>
            <div class="flex justify-between">
              <a class="school-item"
                 href="https://www.dulwich.org/">
                <div class="img-wrap"
                     style="width:174rem">
                  <img src="@/assets/images/s_logo_1.png">
                  <a class="color-green size-18 cursor-pointer more-btn">LEARN MORE &gt;</a>
                </div>

              </a>
              <a class="school-item"
                 href="https://www.dulwich.org/">
                <div class="img-wrap"
                     style="width:237">
                  <img src="@/assets/images/s_logo_2.png">
                  <a class="color-green size-18 cursor-pointer more-btn">LEARN MORE &gt;</a>
                </div>
              </a>
              <a class="school-item"
                 href="https://www.dehong.cn/">
                <div class="img-wrap"
                     style="width:180rem">
                  <img src="@/assets/images/s_logo_3.png">
                  <a class="color-green size-18 cursor-pointer  more-btn">LEARN MORE &gt;</a>
                </div>
              </a>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>

</template>

<script>
import '@/assets/js/iscroll.js'
export default {
  name: 'App',
  data () {
    return {
      showFull: false,
      hideFullText: true,
      myScroll: null
    }
  },
  mounted () {

    document.getElementById('content').addEventListener("transitionend", (e) => {
      console.log('e', e)
      e.preventDefault()
      e.stopPropagation()
      if (e.propertyName === "max-height") {
        if (!this.showFull) {
          this.hideFullText = true
        }
        this.$nextTick(() => {
          this.reloadScroll()
        })
      }


    })

    this.reloadScroll()

  },
  methods: {
    reloadScroll () {
      if (this.myScroll) {
        this.myScroll.destroy()
        this.myScroll = null
      }
      this.myScroll = new IScroll('#wrapper', {
        mouseWheel: true,
        scrollbars: true,
        fadeScrollbars: true
      });
    },
    scrollDown () {
      this.showFull = true
      this.hideFullText = false
    },
    scrollUp () {
      this.showFull = false
      // this.hideFullText = true
    }
  }
}
</script>

<style>
@font-face {
  font-family: "DroidSerif";
  src: url("./assets/font/DroidSerif-Regular.ttf") format("truetype");
}


a {
  text-decoration: none;
}
* {
  padding: 0;
  margin: 0;
  font-size: 0;
  font-family: "DroidSerif";
}
html {
  font-size: 1px;
}
html {
  touch-action: none;
}

body {
  overflow: hidden; /* this is important to prevent the whole page to bounce */
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
@media screen and (max-width: 768px) {
  html {
    font-size: 0.8px;
  }
}
@media screen and (max-width: 512px) {
  html {
    font-size: 0.5px;
  }
}

.gradient {
  height: 36rem;
  background-image: linear-gradient(#fff, rgba(255, 255, 255, 0));
}
@media screen and (max-width: 512px) {
  .gradient {
    height: 36rem;
    background-image: linear-gradient(#fff, rgba(255, 255, 255, 0));
  }
}
.sign img {
  height: 82rem;
}
.logo {
  height: 178rem;
  transition: all 0.2s;
}
.flex {
  display: flex;
}
.justify-between {
  justify-content: space-between;
}
.flex-1 {
  flex: 1;
}
.width-876 {
  width: 876rem;
}
.width-812 {
  width: 812rem;
}
@media screen and (max-width: 812px) {
  .width-812 {
    width: 100%;
  }
}
.min-w-194 {
  min-width: 220rem;
}
/* @media screen and (min-width: 1921px) {
  .wrap {
    width: 1920rem;
    margin: 0 auto;
    box-sizing: border-box;
  }
} */
.wrap {
  padding: 42rem;
  position: relative;
}
.logo-wrap {
  position: fixed;
  width: calc(100% - 7px);
  left: 0;
  top: 0;
  /* padding: 92rem 0 92rem 125rem; */
  z-index: 2;
}
@media screen and (max-width: 512px) {
  .logo-wrap {
    padding: 0;
  }
}
.logo-wrap2 {
  background: #fff;
  padding: 42rem;
}
@media screen and (max-width: 512px) {
  .logo-wrap2 {
    padding: 32rem;
  }
}
/* @media screen and (min-width: 1921px) {
  .logo-wrap2 {
    width: 1920rem;
    margin: 0 auto;
    box-sizing: border-box;
    padding:32rem;
  }
} */

@media screen and (max-width: 512px) {
  .wrap {
    padding: 0 36rem 36rem;
  }
}
.img-wrap {
  width: 237rem;
}
.img-wrap img {
  transition: all 0.5s;
  padding: 0 5px;
  cursor: pointer;
}
.img-wrap img:hover {
  background: #dcdcdc54;
  border-radius: 5px;
}
.school-item {
  text-align: center;
}
.school-item img {
  height: 150rem;
}
@media screen and (max-width: 512px) {
  .school-item img {
    height: 140rem;
  }
}
.color-grey {
  color: #646869;
}
.color-green {
  color: #9ac83b;
  transition: all 0.2s;
}
.color-green:hover {
  color: #628a14;
}
.pb-106 {
  padding-bottom: 106rem;
}
.mb-30 {
  margin-bottom: 30rem;
}
.mb-49 {
  margin-bottom: 49rem;
}
.mb-20 {
  margin-bottom: 20rem;
}
.mb-66 {
  margin-bottom: 66rem;
}
.mb-33 {
  margin-bottom: 33rem;
}
.size-28 {
  font-size: 28rem;
  line-height: 28rem;
}
.size-18 {
  font-size: 18rem;
  line-height: 18rem;
}
@media screen and (max-width: 768px) {
  .size-28 {
    font-size: 35rem;
    line-height: 35rem;
  }
  .size-18 {
    font-size: 22.5rem;
    line-height: 22.5rem;
  }
}
@media screen and (max-width: 512px) {
  .size-28 {
    font-size: 48rem;
    line-height: 48rem;
  }
  .size-18 {
    font-size: 36rem;
    line-height: 36rem;
  }
}
.line-30 {
  line-height: 30rem;
}
@media screen and (max-width: 512px) {
  .line-30 {
    line-height: 48rem;
  }
}
.bold {
  font-weight: bold;
}
.cursor-pointer {
  cursor: pointer;
}
.content {
  margin-top: 250rem;
}
.content .p {
  margin-top: 18rem;
  display: inline-block;
}
@media screen and (max-width: 512px) {
  .content {
    margin-top: 260rem;
  }
}
.content-text.scrollup {
  max-height: 200rem;
}
.schools {
  max-width: 876rem;
}
.content-text {
  transition: all 0.2s;
  max-height: 1000rem;
  overflow: hidden;
}

.hide {
  display: none;
}
@media screen and (max-width: 512px) {
  .content-text.scrollup {
    max-height: 1000rem;
  }
  .content-text {
    max-height: 5000rem;
  }
}
.more-btn {
  margin-top: 32rem;
  text-decoration: none;
  display: block;
  white-space: nowrap;
}
@media screen and (max-width: 512px) {
  .full-btn {
    display: block;
    margin-top: 20rem;
    font-size: 28rem;
  }
  .more-btn {
    font-size: 24rem;
  }
}
</style>
