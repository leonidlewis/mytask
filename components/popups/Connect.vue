<template>
    <div class="connect flex justify-center items-center" :class="{ show: isShow }">
        <div class="overlay" @click.prevent="onClickClose"></div>
        <div class="popup">
            <div class="header flex justify-between mb-10">
                <h2>Connect your wallet</h2>
                <a href="#" class="close-btn" @click.prevent="onClickClose">
                    <img src="~/assets/close-btn.svg" alt="">
                </a>
            </div>
            <div class="body">
                <div class="items flex flex-col">
                    <div class="item flex items-center" @click.prevent="onClickItem(item)"  v-for="(item, index) in items" :key="index">
                        <div class="icon">
                            <img :src="require(`~/assets/${item.icon}`)" alt="" />
                        </div>
                        {{ item.name }}
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'Connect',

    props: ['value'],

    data() {
        return {
            isShow: this.value,
            items: [
                {
                    icon: 'sollet.svg',
                    name: 'Sollet',
                    url: 'https://www.sollet.io/#origin=https%3A%2F%2Fsaber.so&network=https%3A%2F%2Fstableswap.rpcpool.com%2F',
                },
                // {
                //     icon: 'phantom.svg',
                //     name: 'Install Phantom',
                //     url: 'https://phantom.app/',
                // },
                // {
                //     icon: 'sollet.svg',
                //     name: 'Install Sollet Extension',
                //     url: 'https://chrome.google.com/webstore/detail/sollet/fhmfendgdocmcbmfikdcogofphimnkno',
                // }
            ],
        }
    },

    watch: {
        value() {
            this.isShow = this.value
        }
    },

    methods: {
        onClickClose() {
            this.$emit('close')   
        },
        onClickItem(item) {
            const a = document.createElement('a')
            a.target = 'blank'
            a.href = item.url
            a.click();
        }
    }
}
</script>

<style lang="scss" scoped>
    .connect {
        position: fixed;
        left: 0;
        top: 0;
        width: 100vw;
        height: 100vh;
        z-index: -1;
        opacity: 0;
        transition: all .3s;

         .overlay {
            position: absolute;
            z-index: 1;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, .4);
        }
        
        &.show {
            visibility: visible;
            z-index: 999;   
            opacity: 1;
        }

        .popup {
            background: #11102D;
            opacity: 1;
            border-radius: 20px;    
            min-width: 539px;
            padding: 30px;
            z-index: 2;
            position: relative;
            box-shadow: 20px 4px 40px rgba(0, 0, 0, 0.35);
            border-radius: 20px;
            padding: 37px 46px;

            .header {
                font-size: 18px;
                font-style: normal;
                font-weight: 700;
                line-height: 22px;
                letter-spacing: 0em;
                text-align: left;
                color: #fff;
            }

            .items {
                overflow: auto;
                max-height: calc(100vh - 400px);

                .item {
                    background: #1F1E3C;
                    border-radius: 15px;
                    padding: 23px 25px;
                    position: relative;
                    margin: 2px 2px 10px 2px;
                    color: #fff;
                    cursor: pointer;

                    .icon {
                        width: 22px;
                        height: 22px;
                        margin-right: 25px;
                        
                        img {
                            width: 100%;
                            height: 100%;
                            object-fit: cover;
                        }
                    }
                }
            }
        }
    }

    @media (max-width: 768px) {
        .connect .popup {
            min-width: unset;
            width: calc(100vw - 30px);
            height: calc(100vh - 30px);
            padding: 30px 25px;
        }
    }
</style>