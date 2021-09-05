<template>
  <div>
    <section id="hero" class="mycontainer">
      <div class="flex">
        <div class="w-100">
          <div class="hero-box-size">
            <h1 class="center-text h1-fs" id="">Lagrange Roadmap</h1>
          </div>
          <div class="container small-box-size centering">
            <p class="center-text hero-text" id="description">
              The path to unlimited scalability and speed.
            </p>
          </div>
        </div>
      </div>
    </section>
    <section class="pd-container">
      <div class="centering">
        <div class="flex aboutus-box-size pos-rel flex-around tab-wrap">
          <div class="flex-0 tab-car-roadmap">
            <div class="roadmap rotate car-roadmap">
              <div class="first-curve disappear"></div>
              <div class="second-curve"></div>
              <div
                class="tab"
                v-for="(item, index) in tabs"
                :key="'tab-' + index"
                :class="{ active: tab === item }"
                @click="selected(item, index)"
              >
                <div class="spiral car" :class="tab.animation">
                  <img src="~/assets/car.svg" alt="" />
                </div>
                <div
                  class="w-100 rotate-text car-point"
                  :class="[item.point, item.roadmapclass]"
                >
                  <span class="home-roadmap-text roadmap-point-w">
                    {{ item.name }} </span
                  ><span
                    class="home-roadmap-text text-disappear"
                    :class="item.mobclass"
                  >
                    {{ item.name }}
                  </span>
                </div>
              </div>
            </div>
          </div>
          <div class="gallery">
            <div class="tab-pane" v-if="showPhase1">
              <div class="roadmap-card animate-slide">
                <div class="roadmap-card-h flex">
                 <img src="~/assets/logo.svg" alt=""/>
                  <h1 class="small-side-mg roadmap-card-h-text" id="">
                    Phase One
                  </h1>
                  <img src="~/assets/good.svg" alt="" class="good" />
                </div>
                <div class="roadmap-card-b">
                  <h2 class="group-h-grad roadmap-card-b-h" id="">
                    Project Lagrange
                  </h2>
                  <ul class="roadmap-list">
                    <li style="word-break:break-all">
                      Lagrange validator node<br/>
                      <a
                        href="https://www.validators.app/validators/mainnet/8aFVpQCyi7rRnPt2KvyRCygxMKdW12sWvbmHprMp1ZLW?locale=en&refresh=true"
                        target="_blank"
                        >https://www.validators.app/validators/mainnet/8aFVpQCyi7rRnPt2KvyRCygxMKdW12sWvbmHprMp1ZLW?locale=en&refresh=true</a
                      >
                    </li>
                    <li style="word-break:break-all">
                      RPC endpoints: <br/><a
                        href="https://lagrange.rpcpool.com"
                        target="_blank"
                        >https://lagrange.rpcpool.com</a
                      >
                    </li>
                    <li>Creating custom token data bucket</li>
                    <li>Minimal swap feature</li>
                    <li>Integration with Serum on chain orderbook</li>
                    <li>Cross Currency pair calculation</li>
                  </ul>
                </div>
                <div class="roadmap-card-b top-mg">
                  <h2 class="group-h-grad roadmap-card-b-h" id="">
                    LGRN token
                  </h2>
                  <ul class="roadmap-list">
                    <li>Tokenomics</li>
                    <li>Cross Currency Algorithm using LGRNG</li>
                  </ul>
                </div>
              </div>
            </div>
            <div class="tab-pane" v-if="showPhase2">
              <div class="roadmap-card animate-slide">
                <div class="roadmap-card-h flex">
                  <img src="~/assets/logo.svg" alt=""/>
                  <h1 class="small-side-mg roadmap-card-h-text" id="">
                    Phase Two
                  </h1>
                  
                </div>
                <div class="roadmap-card-b">
                  <ul class="roadmap-list">
                    <li>Pools</li>
                    <li>Integration with AMMs</li>
                    <li>Creating LagraSerumUSD_BASK</li>
                    <li>Trade Route optimisation algorithm and pool</li>
                    <li>Arbitrage algorithm and pool</li>
                    <li>Lagrange whitepaper</li>
                    <li>Integration with Lagrange app</li>
                    <li>Token sale</li>
                  </ul>
                </div>
              </div>
            </div>
            <div class="tab-pane" v-if="showPhase3">
              <div class="roadmap-card animate-slide">
                <div class="roadmap-card-h flex">
                  <img src="~/assets/logo.svg" alt=""/>
                  <h1 class="small-side-mg roadmap-card-h-text" id="">
                    Phase Three
                  </h1>
                </div>
                <div class="roadmap-card-b">
                  <ul class="roadmap-list">
                    <li>Solana and Ethereum DEX listing</li>
                    <li>Volume and TVL growth</li>
                    <li>Create your own stablecoin market</li>
                    <li>Integration with Ethereum AMMs</li>
                    <li>Cross-chain swaps</li>
                  </ul>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>
<script>
export default {
  name: "roadmap",

  layout: "app",

  data() {
    return {
      tab: {},
      currentpane: {},
      animateslide: "",
      tabs: [
        {
          name: "Phase1",
          animation: "animate-move-0",
          mobclass: "mob-pos-1",
          roadmapclass: "roadmap-point-1",
          point: "point-1"
        },
        {
          name: "Phase2",
          animation: "animate-move-1",
          mobclass: "mob-pos-2",
          roadmapclass: "roadmap-point-2",
          point: "point-2"
        },
        {
          name: "Phase3",
          animation: "animate-move-2",
          mobclass: "mob-pos-3",
          roadmapclass: "roadmap-point-3",
          point: "point-3"
        }
      ],
      seletedphase: "phase1",
      showPhase1: true,
      showPhase2: false,
      showPhase3: false
    };
  },
  mounted() {
    this.tab = this.tabs[0];
  },
  methods: {
   
    selected(item, index) {
      this.tab = item;
			 switch (index) {
        case 0:
          this.showPhase1 = true;
          this.showPhase2 = false;
          this.showPhase3 = false;
          break;
        case 1:
          this.showPhase1 = false;
          this.showPhase2 = true;
          this.showPhase3 = false;
          break;
        case 2:
          this.showPhase1 = false;
          this.showPhase2 = false;
          this.showPhase3 = true;
          break;
      }
    }
  }
};
</script>

<style lang="scss">
::-webkit-scrollbar {
  width: 10px;
}

/* Track */
::-webkit-scrollbar-track {
  background: #b6b1e4;
}

/* Handle */
::-webkit-scrollbar-thumb {
  background: #1c1647;
}

/* Handle on hover */
::-webkit-scrollbar-thumb:hover {
  background: #070423;
}

@font-face {
  font-family: "Gilroy-Regular";
  font-style: normal;
  font-weight: normal;
  src: url("../src/fonts/Gilroy-Regular.woff") format("woff");
}
@font-face {
  font-family: "Gilroy-Bold";
  font-style: normal;
  font-weight: normal;
  src: url("../src/fonts/Gilroy-Bold.woff") format("woff");
}
@font-face {
  font-family: "DM-Sans-Regular";
  font-style: normal;
  font-weight: normal;
  src: url("../src/fonts/DMSans-Regular.woff") format("woff");
}
@media only screen and (min-width: 1281px) {
  .gallery {
    margin-left: 380px;
  }
}
.mycontainer {
  height: auto;
}
.hero-box-size {
  width: 100%;
  margin: 60px 0 0;
  padding: 0 10vw;
}
.small-box-size {
  width: 50vw;
}
h2 {
  margin-block-start: 0.83em;
}
.pd-container {
  padding: 3vh 6.7vw;
  color: white;
  overflow: hidden;
}
.centering {
  align-items: center;
  align-content: center;
  justify-content: center;
  margin: 0 auto;
  height: auto;
}
#description {
  margin: 1em 0;
}
.center-text {
  text-align: center;
}
.h1-fs {
  font-family: "Gilroy-Bold";
  color: white;
  font-size: 64px;
  font-weight: 700;
  line-height: 74px;
}
.hero-text {
  color: #b3b4c1;
  font-family: "DM-Sans-Regular";
  text-align: center;
  font-size: 20px;
}
.flex {
  display: flex;
}
.aboutus-box-size {
  width: 100%;
  padding: 39px 0;
}
.pos-rel {
  position: relative;
}
.flex-around {
  justify-content: space-around;
}
.flex-0 {
  flex: 0 0;
}
.roadmap {
  border-left: 3px solid;
  border-color: #160d76;
  margin: 160px 0 120px 210px;
  height: 50%;
  position: relative;
}
.car-roadmap {
  top: 30px;
  position: relative;
  height: 360px;
}

.spiral {
  position: absolute;
  left: -39px;
  top: -27px;
  z-index: 2;
  transition: all 1.5s ease;
}
.car {
  left: -20px;
}

@keyframes slide {
  from {
    right: -400px;
  }
  to {
    right: 0;
  }
}

.animate-slide {
  animation: slide 1.5s;
}
.animate-move-0 {
  top: inherit;
  top: -27px;
}
.animate-move-1 {
  top: inherit;
  top: 109px;
}
.animate-move-2 {
  top: inherit;
  top: 245px;
}
.point-1,
.summary-point-1 {
  width: 70%;
  margin: 0 0 100px 50px;
}
.point-2,
.point-3,
.summary-point-2,
.summary-point-3 {
  width: 70%;
  margin: 100px 50px;
}
.point-4,
.summary-point-4 {
  width: 70%;
  margin: 100px 0 0 50px;
}
.roadmap-point-w {
  width: 100%;
}
.point-1:before,
.point-2:before,
.point-3:before,
.summary-point-1:before,
.summary-point-2:before,
.summary-point-3:before,
.summary-point-4:before {
  content: "";
  right: 100%;
  margin-right: -8px;
  position: absolute;
  border-radius: 50%;
  height: 20px;
  width: 20px;
  background-color: #160d76;
}
.w-100 {
  width: 100%;
}
.home-roadmap-text {
  font-family: "Gilroy-Regular";
  font-size: 24px;
  font-style: normal;
  font-weight: bold;
  text-align: left;
  color: #6d6c7d;
}
.tab.active .home-roadmap-text {
  color: #fff;
}
.text-disappear {
  display: none;
}

.gallery {
  width: 420px;
  margin-left: 20%;
}

.roadmap-card {
  line-height: 1.5;
  position: relative;
  width: 450px;
  padding: 50px;
  background-color: #1c1647;
  margin: 20px;
}
.roadmap-card-h {
  width: 90%;
}
.small-side-mg {
  margin-left: 25px;
  color: white;
}
.roadmap-card-h-text {
  font-family: "Gilroy-Regular";
  font-style: normal;
  font-weight: bold;
  font-size: 36px;
}

.good {
  position: absolute;
  right: 95px;
  top: 60px;
}

.roadmap-card-b {
  margin-left: 62px;
}

.roadmap-list {
  font-family: "Gilroy-Regular";
  font-style: normal;
  font-weight: 700;
  list-style: none;
  margin-left: 20px;
}

.roadmap-list > li:before {
  content: "\2022";
  background: -webkit-linear-gradient(#77e3ef, #05aac5);
  -webkit-background-clip: text;
  background-clip: text;
  -webkit-text-fill-color: transparent;
  font-weight: bold;
  font-size: 30px;
  text-align: center;
  display: inline-block;
  width: 1em;
  margin-left: -1em;
}
.group-h-grad {
  background: -webkit-linear-gradient(#77e3ef, #05aac5);
  -webkit-background-clip: text;
  background-clip: text;
  -webkit-text-fill-color: transparent;
}

.roadmap-card-b-h {
  font-family: "Gilroy-Regular";
  font-style: normal;
  font-weight: bold;
  font-size: 24px;
  margin-bottom: 0;
}
.top-mg {
  margin-top: 40px;
}

.first-curve {
  border-bottom: 3px solid;
  border-left: 3px solid;
  border-color: #160d76;
  top: -247px;
  left: -140px;
  width: 100px;
  border-bottom-left-radius: 30px;
  height: 100px;
  padding: 5px 0;
  margin-top: 100px;
  position: absolute;
}

.second-curve {
  border-top: 3px solid;
  border-right: 3px solid;
  border-color: #160d76;
  top: -150px;
  left: -110px;
  width: 110px;
  border-top-right-radius: 30px;
  height: 100px;
  padding: 5px 0;
  margin-top: 100px;
  position: absolute;
}
//mobile responsive
@media only screen and (min-width: 1281px) {
  .gallery {
    margin-left: 380px;
  }
}

@media only screen and (max-width: 1280px) {
  .roadmap-point-w {
    width: 70%;
  }
}

@media only screen and (max-width: 1100px) {
  .h1-fs {
    font-size: 58px;
  }

  .hero-box-size {
    padding: 0 8vw;
  }

  .small-box-size {
    width: 60vw;
  }
  .pd-container {
    padding: 3vh 3.7vw;
  }
}

@media only screen and (max-width: 1024px) {
  .roadmap-point-w {
    width: 70%;
  }

  .hero-box-size {
    padding: 0 6vw;
  }

  .summary-point-1,
  .summary-point-2,
  .summary-point-3,
  .summary-point-4 {
    width: 90%;
  }

  @keyframes slidedown {
    0% {
      top: -27px;
    }
    30% {
      top: -27px;
    }

    33.3% {
      top: 145px;
    }

    63.3% {
      top: 145px;
    }

    66.6% {
      top: 281px;
    }
    96.9% {
      top: 281px;
    }
  }

  .animate-move-0 {
    top: inherit;
    top: -27px;
  }

  .animate-move-1 {
    top: inherit;
    top: 145px;
  }

  .animate-move-2 {
    top: inherit;
    top: 281px;
  }

  .animate-move-to-0 {
    top: inherit;
    top: -27px;
  }

  .animate-move-to-1 {
    top: inherit;
    top: 145px;
  }

  .centering {
    height: auto;
  }
}

@media only screen and (max-width: 920px) {
  .hero-box-size {
    padding: 0 2vw;
  }

  .small-box-size {
    width: 70vw;
  }

  .roadmap {
    margin: 160px 0 120px 160px;
  }

  .summary-point-1,
  .summary-point-2,
  .summary-point-3,
  .summary-point-4 {
    margin: 0 0 80px 40px;
  }

  .mycontainer {
    width: 100%;
  }
}

@media only screen and (max-width: 896px) {
  .point-3 {
    margin: 140px 50px 0;
  }
  .rotate {
    transform: rotate(-90deg);
    transform-origin: left top;
    top: -100px;
    left: -150px;
    height: 380px;
  }

  .tab-car-roadmap {
    height: 0;
  }

  .point-1 span:nth-of-type(2),
  .point-2 span:nth-of-type(2),
  .point-3 span:nth-of-type(2) {
    position: absolute;
    right: -90px;
  }

  .point-1 span:first-of-type,
  .point-2 span:first-of-type,
  .point-3 span:first-of-type {
    visibility: hidden;
  }

  .home-roadmap {
    top: -100px;
    left: 5px;
  }

  .gallery {
    margin-top: 100px;
  }

  .roadmap-point-1 {
    margin: 0 0 140px 50px;
  }
  .roadmap-point-2,
  .roadmap-point-3 {
    margin: 140px 50px 0;
  }

  .mob-pos-1 {
    top: -25px;
    width: 100px;
  }

  .mob-pos-2 {
    bottom: 195px;
    width: 100px;
  }

  .mob-pos-3 {
    bottom: 25px;
    width: 100px;
  }

  .text-disappear {
    display: block;
    transform: rotate(90deg);
    transform-origin: left top;
    left: 60px;
  }

  .disappear {
    display: none;
  }

  .tab-wrap {
    flex-wrap: wrap;
  }

  .home-point-1 {
    margin: 0 0 80px 50px;
  }

  @keyframes slidedown {
    0% {
      top: -27px;
    }
    30% {
      top: -27px;
    }

    33.3% {
      top: 145px;
    }

    63.3% {
      top: 145px;
    }

    66.6% {
      top: 320px;
    }
    96.9% {
      top: 320px;
    }
  }

  .animate-move-0 {
    top: inherit;
    top: -27px;
  }

  .animate-move-1 {
    top: inherit;
    top: 145px;
  }

  .animate-move-2 {
    top: inherit;
    top: 320px;
  }

  .animate-move-to-0 {
    top: inherit;
    top: -27px;
  }

  .animate-move-to-1 {
    top: inherit;
    top: 145px;
  }

  .roadmap-text {
    font-size: 20px;
  }
}

@media only screen and (max-width: 720px) {
  .h1-fs {
    font-size: 54px;
    line-height: 64px;
  }

  .small-box-size {
    width: 60vw;
  }
  .pd-container {
    padding: 3vh 3.7vw;
  }

  .roadmap-point-w {
    width: 70%;
  }

  .rotate {
    margin: 160px 0 0 160px;
  }

  .home-roadmap {
    margin: 160px 0 0 80px;
  }

  .roadmap-point-1 {
    margin: 0 0 140px 50px;
  }
  .roadmap-point-2,
  .roadmap-point-3 {
    margin: 140px 50px 0;
  }

  .mob-pos-1 {
    top: -25px;
    width: 100px;
  }

  .mob-pos-2 {
    bottom: 195px;
    width: 100px;
  }

  .mob-pos-3 {
    bottom: 25px;
    width: 100px;
  }

  .roadmap-text {
    font-size: 16px;
  }

  .summary-point-1,
  .summary-point-2,
  .summary-point-3,
  .summary-point-4 {
    margin: 0 0 40px 20px;
  }
}

@media only screen and (max-width: 550px) {
  body {
    font-size: 16px;
  }

  .hero-box-size {
    padding: 10px;
  }
  .small-box-size {
    width: 80vw;
  }
  .sum-roadmap {
    margin: 110px 0 60px 70px;
  }
  .sum-1 {
    top: -200px;
    left: -70px;
    width: 40px;
    border-bottom-left-radius: 30px;
    height: 55px;
    padding: 5px 0;
  }
  .medium-box-size {
    width: 100%;
  }

  .sum-2 {
    top: -148px;
    left: -40px;
    width: 40px;
    border-top-right-radius: 30px;
    height: 100px;
    padding: 5px 0;
    margin-top: 100px;
    position: absolute;
  }

  .summary-mini-card {
    width: 80%;
    margin: 20px 10px;
  }
  .summary-mini-card-text {
    /* font-size: 16px; */
    color: #fff;
    padding-left: 31px;
  }

  .presale-text {
    width: 90vw;
  }

  .h1-fs {
    font-size: 42px;
    line-height: 45px;
  }

  .home-roadmap {
    margin: 200px 0 0 60px;
    height: 400px;
  }

  .blog-card {
    width: 345px;
    border-radius: 4px;
    margin: 20px 2px;
  }

  .reward .top-mg {
    justify-content: center;
  }

  .fee .small-box-size {
    width: 100%;
    margin-bottom: 60px;
  }

  .section-mg {
    margin-top: 0;
  }

  .reward-card {
    width: 320px;
    height: 280px;
  }
  .reward-card-b {
    font-size: 18px;
  }

  .reward-card-2 {
    width: 300px;
    height: 220px;
  }

  .requirement .small-box-size {
    width: 100%;
    margin-bottom: 100px;
  }

  .home-point-1 .mob-pos-1 {
    left: 100px;
    font-size: 20px;
  }

  .home-point-2 .mob-pos-2 {
    left: 80px;
    font-size: 20px;
  }

  .home-point-3 .mob-pos-3 {
    left: 80px;
    font-size: 20px;
  }
}

@media only screen and (max-width: 450px) {
  .car-roadmap {
    height: 280px;
    left: -120px;
  }

  .roadmap-point-1 {
    margin: 0 0 30px 50px;
  }
  .roadmap-point-2,
  .roadmap-point-3 {
    margin: 90px 50px 0;
  }
  .home-roadmap {
    margin: 200px 0 0 40px;
    height: 300px;
  }

  .roadmap-card {
    margin: 0;
  }

  @keyframes slidedown {
    0% {
      top: -27px;
    }
    30% {
      top: -27px;
    }

    33.3% {
      top: 99px;
    }

    63.3% {
      top: 99px;
    }

    66.6% {
      top: 245px;
    }
    96.9% {
      top: 245px;
    }
  }

  .animate-move-0 {
    top: inherit;
    top: -27px;
  }

  .animate-move-1 {
    top: inherit;
    top: 99px;
  }

  .animate-move-2 {
    top: inherit;
    top: 245px;
  }

  .animate-move-to-0 {
    top: inherit;
    top: -27px;
  }

  .animate-move-to-1 {
    top: inherit;
    top: 99px;
  }

  .mob-pos-1 {
    top: -35px;
    width: 100px;
  }

  .home-point-1 .mob-pos-1 {
    left: 100px;
  }

  .home-point-2 .mob-pos-2 {
    left: 100px;
  }

  .home-point-3 .mob-pos-3 {
    left: 100px;
  }

  .mob-pos-2 {
    bottom: 145px;
    width: 100px;
  }

  .mob-pos-3 {
    bottom: 20px;
    width: 100px;
  }

  .good {
    top: 50px;
    right: 55px;
  }

  .roadmap-card {
    width: 380px;
    padding: 40px 30px;
    margin: 20px 0;
  }

  .home-point-1 {
    margin: 0 0 65px 50px;
  }

  .home-point-2 {
    margin: 0 0 115px 50px;
  }

  .home-point-3 {
    margin: 0 0 0 50px;
  }
  .home-roadmap-text {
    font-size: 20px;
  }

  .hero-text {
    font-size: 18px;
  }
}

@media only screen and (max-width: 380px) {
  .good {
    top: 50px;
    right: 60px;
  }
  .roadmap-card {
    width: 360px;
    padding: 30px 0px;
  }
  .car-roadmap {
    height: 250px;
    left: -110px;
  }

  .home-roadmap {
    margin: 200px 0 0 40px;
    height: 250px;
  }

  .home-point-2 {
    margin: 0 0 70px 50px;
  }

  .roadmap-point-1 {
    margin: 0 0 80px 50px;
  }
  .roadmap-point-2,
  .roadmap-point-3 {
    margin: 80px 50px 0;
  }

  @keyframes slidedown {
    0% {
      top: -27px;
    }
    30% {
      top: -27px;
    }

    33.3% {
      top: 99px;
    }

    63.3% {
      top: 99px;
    }

    66.6% {
      top: 200px;
    }
    96.9% {
      top: 200px;
    }
  }

  .animate-move-0 {
    top: inherit;
    top: -27px;
  }

  .animate-move-1 {
    top: inherit;
    top: 99px;
  }

  .animate-move-2 {
    top: inherit;
    top: 200px;
  }

  .animate-move-to-0 {
    top: inherit;
    top: -27px;
  }

  .animate-move-to-1 {
    top: inherit;
    top: 99px;
  }

  .roadmap-card-h {
    width: 100%;
  }
  .roadmap-list {
    width: 200px;
  }

  .hero-text {
    font-size: 18px;
  }

  .blog-card {
    width: 335px;
    margin: 20px 0;
  }
}

@media only screen and (max-width: 320px) {
  body {
    font-size: 14px;
  }

  .home-point-1 {
    margin: 0 0 35px 50px;
  }

  .voting-card {
    min-width: 300px;
  }

  .hero-text {
    font-size: 16px;
  }

  .grant-card-b {
    font-size: 14px;
  }
  .grant-card {
    height: 400px;
    width: 300px;
    padding: 20px;
  }

  .blog-card {
    width: 315px;
    margin: 20px 0;
  }

  .blog-card-image {
    width: 285px;
    height: 242px;
  }

  .blog-innercard {
    padding: 5px;
  }

  .grant-card-f {
    width: 245px;
    height: 50px;
  }
  .srm-card {
    height: 320px;
  }
  .roadmap-card {
    width: 300px;
    padding: 50px 0px;
  }

  .car-roadmap {
    height: 200px;
    left: -95px;
  }

  .roadmap-point-2,
  .roadmap-point-3 {
    margin: 60px 50px 0;
  }
  @keyframes slidedown {
    0% {
      top: -27px;
    }
    30% {
      top: -27px;
    }

    33.3% {
      top: 69px;
    }

    63.3% {
      top: 69px;
    }

    66.6% {
      top: 170px;
    }
    96.9% {
      top: 170px;
    }
  }

  .animate-move-0 {
    top: inherit;
    top: -27px;
  }

  .animate-move-1 {
    top: inherit;
    top: 69px;
  }

  .animate-move-2 {
    top: inherit;
    top: 170px;
  }

  .animate-move-to-0 {
    top: inherit;
    top: -27px;
  }

  .animate-move-to-1 {
    top: inherit;
    top: 69px;
  }

  .contactus-card {
    width: 300px;
  }

  .good {
    top: 60px;
    right: 10px;
  }

  .mob-pos-2 {
    bottom: 115px;
    width: 100px;
  }
  .roadmap-point-1 {
    margin: 0 0 30px 50px;
  }

  .node-net {
    width: 300px;
    height: 300px;
  }
}
</style>
