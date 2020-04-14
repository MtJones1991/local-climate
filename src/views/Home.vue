<template>
  <div class="home">
    <main>
      <div class="container">
        <div class="row">
          <div class="container">
            <div class="textContainer">
              <div class="animatedText d-flex justify-content-center pb-4">
                <h1 class="aniText anim-typewriter">L o c a l - C l i m a t e</h1>
              </div>
            </div>
            <div class="row">
              <a href="#" class="intro-banner-vdo-play-btn pinkBg" target="_blank">
                <i class="glyphicon glyphicon-play whiteText" aria-hidden="true"></i>
                <span class="ripple pinkBg"></span>
                <span class="ripple pinkBg"></span>
                <span class="ripple pinkBg"></span>
              </a>
            </div>
          </div>
        </div>
      </div>
    </main>
  </div>
</template>

<script>
import moment from "moment";
import router from "../router.js";
// @ is an alias to /src

export default {
  name: "home",
  components: {},
  data() {
    return {};
  },

  methods: {},

  mounted() {
    setTimeout(() => {
      router.push("about");
    }, 4500);
  }
};
</script>

<style scoped>
.jumbotron {
  background-color: #ecba1600;
}

.pinkBg {
  background-color: #ed184f !important;
  background-image: linear-gradient(90deg, #fd5581, #fd8b55);
}

.intro-banner-vdo-play-btn {
  height: 60px;
  width: 60px;
  position: absolute;
  top: 50%;
  left: 50%;
  text-align: center;
  margin: -30px 0 0 -30px;
  border-radius: 100px;
  z-index: 1;
}

.intro-banner-vdo-play-btn i {
  line-height: 56px;
  font-size: 30px;
}

.intro-banner-vdo-play-btn .ripple {
  position: absolute;
  width: 160px;
  height: 160px;
  z-index: -1;
  left: 50%;
  top: 50%;
  opacity: 0;
  margin: -80px 0 0 -80px;
  border-radius: 100px;
  -webkit-animation: ripple 1.8s infinite;
  animation: ripple 1.8s infinite;
}

@-webkit-keyframes ripple {
  0% {
    opacity: 1;
    -webkit-transform: scale(0);
    transform: scale(0);
  }

  100% {
    opacity: 0;
    -webkit-transform: scale(1);
    transform: scale(1);
  }
}

@keyframes ripple {
  0% {
    opacity: 1;
    -webkit-transform: scale(0);
    transform: scale(0);
  }

  100% {
    opacity: 0;
    -webkit-transform: scale(1);
    transform: scale(1);
  }
}

.intro-banner-vdo-play-btn .ripple:nth-child(2) {
  animation-delay: 0.3s;
  -webkit-animation-delay: 0.3s;
}

.intro-banner-vdo-play-btn .ripple:nth-child(3) {
  animation-delay: 0.6s;
  -webkit-animation-delay: 0.6s;
}

/* 
ANIMATED TEXT
*/

/* Global */

.textContainer {
  padding-top: 73%;
}

.aniText {
  font-family: "Orbitron", sans-serif !important;
  color: #fff !important;
  position: relative;
  top: 50%;
  width: 24em;
  margin: 0 auto;
  border-right: 2px solid rgba(255, 255, 255, 0.75);
  font-size: 180%;
  text-align: center;
  white-space: nowrap;
  overflow: hidden;
  transform: translateY(-50%);
}

.aniDescription {
  font-family: "Orbitron", sans-serif !important;
  color: #fff !important;
  position: relative;
  top: 50%;
  width: 21em;
  margin: 0 auto;
  border-right: 2px solid rgba(255, 255, 255, 0.75);
  font-size: 140%;
  text-align: center;
  white-space: nowrap;
  overflow: hidden;
  transform: translateY(-50%);
}

.aniHeader {
  font-family: "Orbitron", sans-serif !important;
  color: #fff !important;
  position: relative;
  top: 50%;
  width: 21em;
  margin: 0 auto;
  border-right: 2px solid rgba(255, 255, 255, 0.75);
  font-size: 140%;
  text-align: center;
  white-space: nowrap;
  overflow: hidden;
  transform: translateY(-50%);
}

/* Animation */
.anim-typewriter {
  animation: typewriter 1.7s steps(21) 1s 1 normal both,
    blinkTextCursor 650ms steps(21) infinite normal;
}
@keyframes typewriter {
  from {
    width: 0;
  }
  to {
    width: 12em;
  }
}
@keyframes blinkTextCursor {
  from {
    border-right-color: rgba(255, 255, 255, 0.75);
  }
  to {
    border-right-color: transparent;
  }
}

.header-headerwriter {
  animation: headerwriter 3s steps(55) 4s 1 normal both,
    blinkTextCursor 650ms steps(55) infinite normal;
}
@keyframes headerwriter {
  from {
    width: 0;
  }
  to {
    width: 15.5em;
  }
}
@keyframes blinkTextCursor {
  from {
    border-right-color: rgba(255, 255, 255, 0.75);
  }
  to {
    border-right-color: transparent;
  }
}

.desc-descwriter {
  animation: descwriter 3s steps(55) 4s 1 normal both,
    blinkTextCursor 650ms steps(55) infinite normal;
}
@keyframes descwriter {
  from {
    width: 0;
  }
  to {
    width: 14em;
  }
}
@keyframes blinkTextCursor {
  from {
    border-right-color: rgba(255, 255, 255, 0.75);
  }
  to {
    border-right-color: transparent;
  }
}

.zoom {
  transition: transform 0.4s; /* Animation */
}

.zoom:hover {
  transform: scale(
    1.5
  ); /* (150% zoom - Note: if the zoom is too large, it will go outside of the viewport) */
}
</style>
