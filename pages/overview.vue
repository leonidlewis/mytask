<template>
    <div class="overview-wrapper">
        <div class="container mx-auto h-full flex items-center justify-center">
            <div class="overview">
                 <div class="overview-header flex items-center justify-center">
                    <h2>Overview</h2>
                </div>
                <div class="overview-body">
                    <div class="accordion">
                        <div class="items flex flex-col">
                            <div :class="{'open': toggles[index]}" @click.prevent="onClickToggle(index)" class="item" v-for="(overview, index) in overviews" :key="index">
                                <div class="head flex items-center justify-between">
                                    <div class="currency flex items-center">
                                        <div class="from">
                                            <img :src="require(`~/assets/${overview.currencyFrom.icon}.svg`)" alt="" />
                                        </div>
                                        <div class="to ml-3">
                                            <img :src="require(`~/assets/${overview.currencyTo.icon}.svg`)" alt="" />
                                        </div>
                                    </div>
                                    <div class="label mr-auto">
                                        {{ overview.currencyFrom.label }}/{{ overview.currencyTo.label }}
                                    </div>
                                    <a href="#" class="toggle" >
                                        <img src="~/assets/arrow-up.svg" alt="" />
                                    </a>
                                </div>
                                <div class="stacked flex justify-between">
                                    Total Stacked
                                    <span class="ml-auto">
                                        {{ overview.totalStacked }}
                                    </span>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    layout: 'app',

    data() {
        return {
            toggles: {},
            overviews: [
                {
                    currencyFrom: {
                        icon: 'USDT',
                        label: 'USDT',
                    },
                    currencyTo: {
                        icon: 'EURO-L',
                        label: 'EURO-L',
                    },
                    totalStacked: '0,18971'
                },
                {
                    currencyFrom: {
                        icon: 'USDT',
                        label: 'USDT',
                    },
                    currencyTo: {
                        icon: 'BRZ',
                        label: 'BRZ',
                    },
                    totalStacked: '0,18971'
                },
                {
                    currencyFrom: {
                        icon: 'EURO-L',
                        label: 'EURO-L',
                    },
                    currencyTo: {
                        icon: 'USDT',
                        label: 'USDT',
                    },
                    totalStacked: '0,18971'
                },
                {
                    currencyFrom: {
                        icon: 'EURO-L',
                        label: 'EURO-L',
                    },
                    currencyTo: {
                        icon: 'BRZ',
                        label: 'BRZ',
                    },
                    totalStacked: '0,18971'
                },
                {
                    currencyFrom: {
                        icon: 'BRZ',
                        label: 'BRZ',
                    },
                    currencyTo: {
                        icon: 'EURO-L',
                        label: 'EURO-L',
                    },
                    totalStacked: '0,18971'
                },
                {
                    currencyFrom: {
                        icon: 'BRZ',
                        label: 'BRZ',
                    },
                    currencyTo: {
                        icon: 'USDT',
                        label: 'USDT',
                    },
                    totalStacked: '0,18971'
                },
            ]
        }
    },

    mounted() {
        this.reset();
    },

    methods: {
        reset() {
            this.toggles = this.overviews.map(item => {
            return false
        })
        },
        onClickToggle(index) {
            const oldValue = this.toggles[index]
            this.reset();
            this.toggles[index] = ! oldValue
            this.toggles = [...this.toggles]
        }
    }
}
</script>

<style lang="scss">
    .overview-wrapper {
        color: #fff;
        padding: 50px 0;

        .overview {
            background: #11102D;
            box-shadow: 20px 4px 40px rgba(22, 23, 49, 0.15);
            border-radius: 20px;
            padding: 37px 46px;
            min-width: 539px;
        }

        .overview-header {
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

        .items {
            .item {
                margin-bottom: 15px;
                background: #1F1E3C;
                border-radius: 15px;
                padding: 19px 5px 19px 22px;
                transition: all .3s;
                max-height: 78px;
                overflow: hidden;
                cursor: pointer;

                .stacked {  
                    font-size: 14px;
                    font-style: normal;
                    font-weight: 400;
                    line-height: 17px;
                    letter-spacing: 0em;
                    text-align: left;
                    color: #A6A0BB;
                    margin-top: 25px;
                    margin-right: 17px;

                    span {
                        color: #fff;
                    }
                }

                .toggle {
                    transform: rotate(-180deg);
                    transition: all .3s;
                    padding: 15px;
                }

                &.open {
                    max-height: 123px;

                    .toggle {
                        transform: rotate(0deg);
                    }

                    .stacked {
                    }
                }

                .label {
                    font-size: 18px;
                    font-style: normal;
                    font-weight: 700;
                    line-height: 22px;
                    letter-spacing: 0em;
                    text-align: left;
                    margin-left: 25px;
                }

                .to,
                .from {
                    width: 38px;
                    height: 38px;

                    img {
                        width: 100%;
                        height: 100%;
                        object-fit: cover;
                    }
                }
            }
        }
    }


    @media (max-width: 768px) {
        .overview-wrapper {
            .overview {
                width: calc(100vw - 30px);
                min-width: unset;
                padding: 30px 25px;

                .items {
                    .item {
                        padding: 15px;
                        .label {
                            margin-left: 13px;
                        }
                    }
                }
            }
        }
    }
</style>