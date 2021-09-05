<template>
  <main class="h-full">
    <section class="main h-full pt-5 flex flex-col justify-between items-center">
      <navbar class="container mx-auto" @connect="onConnect"/>
      <div class="hero flex justify-center flex-col mt-auto">
        <h1>
          Decentralized<br />
          Bureau de Change
        </h1>
        <span class="my-5 sub-title">Ecosystem-wide. Minimum Slippage. Unlimited opportunities.</span>
      </div>
      <div class="actions flex flex-col items-center mt-5 mb-auto">
        <a href="/swap" class="btn btn-launch">Direct to swap</a>
        <a href="/roadmap" class="mt-5 read-more flex">
          Direct to roadmap
          <img class="ml-3" src="~/assets/read-more-arrow.svg" alt="">
        </a>
      </div>
    </section>

    <section class="functionalities">
      <span class="ball-2">
        <img src="~/assets/ball-2.svg" alt="">
      </span>
      <div class="container mx-auto">
        <h1 class="eco-system-wide">
          <a href="#">Eco System-wide</a> integration for liquidity
        </h1>
        <div class="parts">
          <div class="part">
            <h2>Functionalities</h2>
            <p>This model opens unlimited opportunities including:</p>
            <div class="items">
              <div class="item">
                <img src="~/assets/checked-icon.svg" alt="">
                Cross-pair trading
              </div>
              <div class="item">
                <img src="~/assets/checked-icon.svg" alt="">
                Cross-triangle arbitrage
              </div>
              <div class="item">
                <img src="~/assets/checked-icon.svg" alt="">
                Instant swaps
              </div>
              <div class="item">
                <img src="~/assets/checked-icon.svg" alt="">
                The most possible liquidity
              </div>
              <div class="item">
                <img src="~/assets/checked-icon.svg" alt="">
                Decentralized FX
              </div>
              <div class="item">
                <img src="~/assets/checked-icon.svg" alt="">
                More others
              </div>
            </div>
            <!-- <button class="btn btn-launch">Try it Now</button> -->
          </div>
          <div class="part">
          </div>
          <div class="image">
            <img src="~/assets/image-2.svg" alt="image" />
            <span class="ball">
              <img src="~/assets/ball-1.svg" alt="ball" />
            </span>
          </div>
        </div>
      </div>
    </section>

    <section class="pools">
      <div class="container mx-auto">
        <div class="parts">
          <div class="part">
            <span class="balls">
              <img class="ball-1" src="~/assets/pools-ball-1.png" alt="ball-1" />
              <img class="ball-2" src="~/assets/pools-ball-2.png" alt="ball-2">
            </span>
            <div class="earth">
              <img src="~/assets/earth-part-1.svg" class="part-1" alt="earth" />
              <img src="~/assets/earth-part-2.svg" class="part-2" alt="earth" />
              <img src="~/assets/earth-part-3.svg" class="part-3" alt="earth" />
              <img src="~/assets/earth-part-4.svg" class="part-4" alt="earth" />
            </div>
          </div>
          <div class="part">
            <h2>Pools</h2>
              <p>
                Optimization. Stability. Arbitrage. Different pools have different <br />
                purposes. Evolving based on the historical data.
              </p>
              <!-- <button class="btn btn-launch">Launch App</button> -->
            <img class="ball" src="~/assets/pools-ball-1.png" alt="ball-1" />
          </div>
        </div>
      </div>
    </section>

    <section class="lagrange">
      <div class="container mx-auto">
        <h2>Lagrange</h2>
        <p>
          Mathematical models built using Lagrange multipliers to maximize profit, minimize loss.
        </p>
        <div class="area">
          <div class="overlay">
            <table>
              <tbody>
                <tr>
                  <td>&nbsp;</td>
                  <td>&nbsp;</td>
                  <td>&nbsp;</td>
                  <td>&nbsp;</td>
                  <td>&nbsp;</td>
                </tr>
                <tr>
                  <td>&nbsp;</td>
                  <td>&nbsp;</td>
                  <td>&nbsp;</td>
                  <td>&nbsp;</td>
                  <td>&nbsp;</td>
                </tr>
                <tr>
                  <td>&nbsp;</td>
                  <td>&nbsp;</td>
                  <td>&nbsp;</td>
                  <td>&nbsp;</td>
                  <td>&nbsp;</td>
                </tr>
                <tr>
                  <td>&nbsp;</td>
                  <td>&nbsp;</td>
                  <td>&nbsp;</td>
                  <td>&nbsp;</td>
                  <td>&nbsp;</td>
                </tr>
                <tr>
                  <td>&nbsp;</td>
                  <td>&nbsp;</td>
                  <td>&nbsp;</td>
                  <td>&nbsp;</td>
                  <td>&nbsp;</td>
                </tr>
              </tbody>
            </table>
          </div>
          <span class="ball">
            <img src="~/assets/ball-1.svg" alt="ball" />
          </span>
          <span class="formula">
            \mathcal{L} (x,\lambda) = <span>f(x) - \lambda g(x)</span>
          </span>
        </div>
        <div class="flex justify-center">
          <a class="btn btn-launch" href="/swap">Try it now</a>
        </div>
      </div>
    </section>

    <div class="balls">
      <span class="left">
        <img src="~/assets/footer-part-1.png" alt="assets" />
      </span>
      <span class="right">
        <img src="~/assets/footer-part-2.png" alt="assets" />
      </span>
    </div>

    <footer class="footer p-5">
      <div class="container mx-auto flex justify-between items-center">
        <a href="#">
          <img src="~/assets/logo-v2.svg" alt="logo" />
        </a>
        <div class="navs">
          <a href="#" class="nav">Home</a>
          <a href="#" class="nav">App</a>
          <a href="#" class="nav">Info</a>
        </div>
        <div class="socials">
          <a href="#" class="social">
            <i class="fab fa-facebook-f"></i>
          </a>
          <a href="#" class="social">
            <i class="fab fa-linkedin-in"></i>
          </a>
          <a href="#" class="social">
            <i class="fab fa-twitter"></i>
          </a>
          <a href="#" class="social">
            <i class="fab fa-instagram"></i>
          </a>
          <a href="#" class="social">
            <i class="fab fa-youtube"></i>
          </a>
        </div>
      </div>
    </footer>
    <connect-pop-up v-model="isShowConnect"  @close="isShowConnect = false" />
  </main>
</template>

<script>
import ConnectPopUp from '~/components/popups/Connect';
export default {
   components: {
        connectPopUp: ConnectPopUp,
    },
    data() {
        return {
            isShowConnect: false,
        }
    },
    methods: {
        onConnect() {
            this.isShowConnect = true
            
        }
    }
}
</script>

<style lang="scss">
    body {
    font-family: Sora;
    background: linear-gradient(251.24deg, #282851 10.79%, #0d0331 80.65%);
  }
</style>

<style lang="scss" scoped>
  main {
    position: relative;

}

  .main {
    background-image: url(~/assets/mask.png);
    background-position: center center;
    background-size: cover;
    background-repeat: no-repeat;
    color: #B9B9D9;
    min-height: 100vh;
    position: relative;
    z-index: 1;

    .hero {
      h1 {
        font-size: 92px;
        font-style: normal;
        font-weight: 400;
        line-height: 101px;
        letter-spacing: 0em;
        text-align: center;
        color: #fff;
      }

      span {
        font-size: 18px;
        font-style: normal;
        font-weight: 300;
        line-height: 32px;
        letter-spacing: 0em;
        text-align: center;
      }
    }

    .btn-launch {
      background: linear-gradient(95.17deg, #60C3F4 -3.23%, #E479F0 105.35%);
      border-radius: 112px;
      padding: 15px 55px;
      color: #fff;
    }

    .read-more {
      font-size: 14px;
      font-style: normal;
      font-weight: 300;
      letter-spacing: 0em;
      text-align: center;
      color: #fff;
    }
  }

  .functionalities {
    color: #fff;
    font-family: Sora;
    padding: 100px 50px 250px 50px;

    overflow: hidden;
    position: relative;
    z-index: 1;

    .ball-2 {
      position: absolute;
      z-index: 2;
      width: 200px;
      height: 200px;
      top: 50px;
    }

    h1 {
        font-size: 56px;
        font-style: normal;
        font-weight: 300;
        letter-spacing: 0em;
        white-space: nowrap;
        color: #fff;

        a {
          font-weight: 400;
          color: #7fb2f2;
        }
    }

    .parts {
      display: grid;
      grid-template-columns: 1fr 1fr;
      grid-gap: 100px;
      margin-top: 120px;

      .image {
        position: absolute;
        right: 0;
        top: 150px;
        width: 50%;

        .ball {
          width: 150px;
          height: 150px;
          position: absolute;
          top: 15%;
          right: 10%;
          z-index: 1;
        }
      }
    }

    .part {
      position: relative;
      z-index: 0;

      .image {
        img {
          object-fit: cover;
          object-position: center center;
          width: 100%;
          height: 100%;
        }
      }

      p {
        font-size: 18px;
        font-style: normal;
        font-weight: 300;
        line-height: 32px;
        letter-spacing: 0em;
        text-align: left;
        color: #B9B9D9;
        padding: 16px 0 50px;
      }

      h2 {
        font-size: 64px;
        font-style: normal;
        font-weight: 300;
        letter-spacing: 0em;

        a {
          font-weight: 400;
        }
      }

      .items {
        display: grid;
        grid-template-columns: 1fr 1fr;

        .item {
          display: flex;
          align-items: center;
          margin-bottom: 32px;
          font-size: 20px;
          white-space: nowrap;
          margin-left: 20px;

          img {
            margin-right: 20px;
          }
        }
      }
    }
  }

  .footer {
    background: #28274D;
    font-size: 16px;
    font-style: normal;
    font-weight: 300;
    line-height: 20px;
    letter-spacing: 0em;
    text-align: center;
    position: relative;

    .navs {
      color: #B9B9D9;

      display: grid;
      grid-template-columns: 1fr 1fr 1fr;
      grid-gap: 80px;
    }

    .socials {
      display: grid;
      grid-template-columns: 1fr 1fr 1fr 1fr 1fr;
      grid-gap: 16px;

      .social {
        color: #fff;
        display: inline-block;
        width: 35px;
        height: 35px;
        border-radius: 50%;
        background-color: #363559;
        display: flex;
        justify-content: center;
        align-items: center;
      }
    }
  }

  .balls {
    display: grid;
    grid-template-columns: 1fr 1fr;
    position: absolute;
    bottom: 0;
    left: 0;
    right: 0;

    .left img,
    .right img {
      object-fit: cover;
      height: 100%;
      width: 100%;
    }
  }

  .pools {
    color: #fff;
    margin-bottom: 200px;

    .btn-launch {
      padding-left: 50px;
      padding-right: 50px;
      font-size: 16px;
    }

    .parts {
      display: grid;
      grid-template-columns: 1fr 1fr;
      grid-gap: 100px;

      .part {
        font-size: 23px;
        position: relative;

        .earth {
          position: relative;
          height: 362px;
          width: 362px;
          margin-left: auto;

          .part-1,
          .part-2,
          .part-3,
          .part-4 {
            position: absolute;
          }

          .part-1,
          .part-2,
          .part-4 {
            width: 100%;
            height: 100%;
          }

          .part-3 {
            bottom: -20px;
            left: -15px;
            background: radial-gradient(39.08% 39.02% at 52.92% 53.69%, #A39DF2 0%, #8A8AF0 17%, #3D3A94 31%, #333333 43%, #181818 58%, #0B0B0B 75%, #050505 87%, #000000 100%);
            background-blend-mode: screen;
            mix-blend-mode: screen;
            opacity: 0.3;
          }

          .part-4 {
            background: radial-gradient(38.78% 38.71% at 49.68% 50.01%, #EBEBEB 0%, #C5C5C5 14%, #A2A2A2 24%, #636363 39%, #3D3D3D 55%, #2B2B2B 65%, #1F1F1F 75%, #0C0C0C 87%, #000000 100%);
            background-blend-mode: color-dodge;
            mix-blend-mode: color-dodge;
            transform: matrix(0.8, -0.6, 0.6, 0.8, 0, 0);
            top: -20%;
            right: -20%;
          }
        }

        .balls {
          position: absolute;
          display: block;
          top: -150px;
          right: 0;
          width: 251px;
          height: 251px;

          .ball-1,
          .ball-2 {
            position: absolute;
            left: 0;
          }

          .ball-1 {
            bottom: -35px;
            left: -35px;
          }

          .ball-2 {
            top: 0;
          }
        }

        .ball {
          position: absolute;
          bottom: -150px;
          width: 85px;
          height: 85px;
          right: 0;
        }

        h2 {
          font-size: 64px;
          font-style: normal;
          font-weight: 400;
          line-height: 80px;
          letter-spacing: 0em;
          text-align: left;
        }

        p {
          font-size: 18px;
          font-style: normal;
          font-weight: 300;
          line-height: 32px;
          letter-spacing: 0em;
          text-align: left;
          color: #B9B9D9;
          padding: 16px 0 40px;
        }
      }
    }
  }

  .lagrange {
    h2 {
      font-size: 64px;
      font-style: normal;
      font-weight: 400;
      line-height: 80px;
      letter-spacing: 0em;
      text-align: left;
      color: #fff;
      text-align: center;
    }

    p {
      font-size: 18px;
      font-style: normal;
      font-weight: 300;
      line-height: 32px;
      letter-spacing: 0em;
      text-align: left;
      color: #B9B9D9;
      text-align: center;
      margin: 16px 0 40px;
    }

    .area {
      background: linear-gradient(260.95deg, #29284D -1.14%, #282750 100.76%);
      min-height: 445px;
      border-radius: 32px;
      box-shadow: 20px 4px 40px 0px #1617310F;
      padding: 30px;
      max-width: 1152px;
      margin: 0 auto 50px;
      text-align: center;
      position: relative;
      z-index: 0;

      .overlay {
        position: absolute;
        z-index: 1;
        top: 0;
        left: 0;
        right: 0;
        bottom: 0;
        border-radius: 32px;
        overflow: hidden;

        table {
          border-collapse: collapse;
          width: 100%;
          height: 100%;

        }
      }

      table,
      td,
      th {
        border: 1px solid #1D1D44;
      }

      .ball {
        position: absolute;
        z-index: 2;
        top: 15px;
        left: -160px;
        width: 304px;
        height: 304px;
      }

      .formula {
        color: #fff;
        margin: 70px auto;
        display: inline-block;
        position: relative;
        padding: 16px 25px;
        font-size: 24px;
        z-index: 2;

        span {
          color: #E479F0;
        }

        &:after {
          content: '';
          display: inline-block;
          position: absolute;
          z-index: 2;
          left: -25%;
          right: -25%;
          top: -25%;
          bottom: -25%;
          background-image: url(~/assets/formula-border.png);
          background-repeat: no-repeat;
          background-size: contain;
          background-position: center center;
        }
      }

      &:before {
        content: '';
        display: inline-block;
        position: absolute;
        z-index: 2;
        left: -10%;
        right: -10%;
        top: -10%;
        bottom: -10%;
        background-image: url(~/assets/line-curved.svg);
        background-repeat: no-repeat;
        background-size: contain;
        background-position: center center;
      }
    }

    .btn {
      margin-bottom: 150px;
    }
  }

  .btn-launch {
    background: linear-gradient(95.17deg, #60C3F4 -3.23%, #E479F0 105.35%);
    border-radius: 112px;
    padding: 15px 85px;
    color: #fff;
    z-index: 2;
  }

  @media (max-width: 1024px) {
    .container {
      padding: 0 30px;
    }

    .functionalities  {
      h1 {
        white-space: normal;
      }

      .parts {
         .image {
          .ball {
            width: 55px;
            height: 55px;
          }
        }
      }

      .part {
        .items {
          margin-bottom: 50px;

          .item {
            white-space: normal;
            margin-bottom: 10px;
          }
        }
      }
    }

    .lagrange {
      .area {
        &:before {
          left: 0%;
          right: 0%;
        }
      }
    }
  }

  @media (max-width: 768px) {
    .main {
      .hero {
        margin-top: 20vh;

        h1 {
          font-size: 44px;
          line-height: normal;
        }
      }

      .actions {
        margin-bottom: 50px;
      }
    }


    .pools {
      .parts {
        grid-template-columns: 1fr;

        .part {
          text-align: center;

          .earth {
            margin: 0 auto;
            overflow: hidden;
            height: 300px;
            width: 300px;
          }

          h2 {
            text-align: center;
            font-size: 45px;
          }

          p {
            text-align: center;
          }
        }
      }
    }

    .functionalities {
      padding: 100px 0 150px;

      .eco-system-wide {
        font-size: 45px;
        line-height: normal;
      }

      .parts {
        grid-template-columns: 1fr;

        h2 {
          font-size: 45px;
        }

        .items {
          grid-template-columns: 1fr;
        }
      }
    }

    .lagrange {
      .container {
        overflow: hidden;
      }

      h2 {
        font-size: 45px;
      }

      .btn-launch {
        margin-bottom: 50px;
      }
    }

    .footer {
      .container {
        flex-direction: column;
      }

      .navs {
        margin: 15px 25px;
        grid-gap: 5px;
      }
    }
  }
</style>
