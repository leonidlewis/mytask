<template>
  <div class="swap-wrapper">
    <div class="container mx-auto h-full flex items-center justify-center">
      <div class="swap">
        <div class="swap-header flex items-center justify-center">
          <h2 class="ml-auto">Swap</h2>
          <a href="#" class="ml-auto" @click.prevent="isShowSettings = true">
            <img src="~/assets/settings-icon.svg" alt="settings-icon" />
          </a>
        </div>
        <div class="swap-body">
          <div class="swap-items flex flex-col">
            <div class="swap-item item-from">
              <div class="title flex">
                Balance: {{ from.ballance }} {{ from.currency.label }}
                <span class="in-dolars">
                  ~$120
                </span>
              </div>
              <div class="amount mt-3 flex items-center justify-between">
                <input
                  title=""
                  type="text"
                  :value="from.amount"
                  class="amount_input"
                  @keypress="isNumber($event)"
                />
                <!-- {{ from.amount }} -->
                <div class="currency">
                  <currency-dropdown v-model="from.currency" />
                </div>
              </div>
            </div>
            <a
              href="#"
              @click.prevent="onClickExchange"
              class="btn btn-exchange flex justify-center items-center"
            >
              <img src="~/assets/exchange-icon.svg" alt="exchange" />
            </a>
            <div class="swap-item item-from">
              <div class="title flex">
                Balance: {{ to.ballance }} {{ to.currency.label }}
                <span class="in-dolars ml-auto">
                  ~$120 <span class="calc">(0.04002%)</span>
                </span>
              </div>
              <div class="amount mt-3  flex items-center justify-between">
                {{ to.amount }}
                <div class="currency">
                  <currency-dropdown v-model="to.currency" />
                </div>
              </div>
            </div>
            <div class="swap-rate my-8 flex items-center">
              <span class="mr-2">
                <img
                  src="~/assets/exchange-icon-gray.svg"
                  alt="exchange-icon-gray"
                />
              </span>
              Exchange Rate
              <span class="rate ml-auto"
                >1 {{ from.currency.label }} = 0.99999
                {{ to.currency.label }}</span
              >
            </div>
          </div>
          <div class="swap-footer">
            <button class="btn btn-connect" @click.prevent="onConnect">
              Connect Wallet
            </button>
          </div>
        </div>
      </div>
    </div>
    <settings-pop-up v-model="isShowSettings" @close="isShowSettings = false" />
  </div>
</template>

<script>
import SettingsPopUp from "~/components/popups/Settings";
import CurrencyDropdown from "~/components/CurrencyDropdown";

export default {
  name: "swap",

  components: {
    SettingsPopUp,
    CurrencyDropdown
  },

  layout: "app",

  data() {
    return {
      isShowSettings: false,
      from: {
        ballance: "0.00000",
        amount: 120,
        currency: {
          icon: "USDC",
          label: "USDC"
        }
      },
      to: {
        ballance: "0.00000",
        amount: 119.993716,
        currency: {
          icon: "USDT",
          label: "USDT"
        }
      }
    };
  },

  methods: {
    isNumber: function(evt) {
      evt = evt ? evt : window.event;
      var charCode = evt.which ? evt.which : evt.keyCode;
      if (
        charCode > 31 &&
        (charCode < 48 || charCode > 57) &&
        charCode !== 46
      ) {
        evt.preventDefault();
      } else {
        return true;
      }
    },
    onConnect() {
      this.$nuxt.$emit("connect");
    },
    onClickExchange() {
      const temp = this.from;
      this.from = this.to;
      this.to = temp;
    }
  }
};
</script>

<style lang="scss">
.swap-wrapper {
  color: #fff;
  padding: 50px 0;

  .swap {
    background: #11102d;
    box-shadow: 20px 4px 40px rgba(22, 23, 49, 0.15);
    border-radius: 20px;
    padding: 37px 46px;
    min-width: 539px;

    .swap-header {
      margin-bottom: 45px;

      h2 {
        font-size: 24px;
        font-style: normal;
        font-weight: 700;
        line-height: 29px;
        letter-spacing: 0em;
        text-align: center;
      }
    }

    .swap-body {
      .btn-exchange {
        background: #1f1e3b;
        border-radius: 50%;
        width: 40px;
        height: 40px;
        margin: 8px auto;
        display: inline-block;

        img {
          width: 100%;
          height: 100%;
          object-fit: scale-down;
        }
      }

      .swap-items {
        .swap-item {
          background: #1f1e3c;
          border-radius: 15px;
          padding: 16px 17px 17px;

          .title {
            font-size: 16px;
            font-style: normal;
            font-weight: 400;
            line-height: 19px;
            letter-spacing: 0em;
            color: #a6a0bb;

            span {
              color: #fff;
              margin-left: auto;
            }
          }

          .amount {
            font-size: 30px;
            font-style: normal;
            font-weight: 800;
            line-height: 36px;
            letter-spacing: 0em;
          }
          .amount_input {
            font-size: 30px;
            font-style: normal;
            font-weight: 800;
            line-height: 36px;
            letter-spacing: 0em;
            background: transparent;
            border: none;
            max-width: 307px;
            @media (max-width: 768px) {
              max-width: 543px;
              width: 543px;
              font-size: 23px;
            }
            @media (max-width: 414px) {
              max-width: 194px;
            }
            @media (max-width: 376px) {
              max-width: 155px;
            }
            @media (max-width: 360px) {
              max-width: 140px;
            }
            @media (max-width: 320px) {
              max-width: 114px;
            }
          }

          //   .amount_input:focus{
          //       color:transparent;
          //       text-shadow: 0px 0px 0px white;
          //   }
          .amount_input:focus-visible {
            outline: none;
          }

          .amount_input::-webkit-outer-spin-button,
          .amount_input::-webkit-inner-spin-button {
            -webkit-appearance: none;
            margin: 0;
          }
          .in-dolars {
            .calc {
              color: #1fe0b0;
            }
          }

          &.item-from {
          }

          &.item-to {
          }
        }
      }

      .swap-rate {
        color: #a6a0bb;

        .rate {
          color: #ffff;
        }
      }
    }

    .swap-footer {
      .btn-connect {
        background: linear-gradient(
          90deg,
          #c734f7 0.35%,
          #8c72da 57.62%,
          #7890d3 99.2%
        );
        box-shadow: 20px 4px 40px rgba(22, 23, 49, 0.15);
        border-radius: 112px;
        width: 100%;
        padding: 14px;
        font-style: normal;
        font-weight: bold;
        font-size: 18px;
        line-height: 120%;
      }
    }
  }
}

@media (max-width: 768px) {
  .swap-wrapper {
    .swap {
      width: calc(100vw - 30px);
      min-width: unset;
      padding: 30px 25px;

      .swap-body {
        .swap-items {
          .swap-item {
            .amount {
              font-size: 23px;
            }
          }
        }
      }
    }
  }
}
</style>
