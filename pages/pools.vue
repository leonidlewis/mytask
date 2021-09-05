<template>
    <div class="pool-wrapper">
        <div class="container mx-auto h-full flex items-center justify-center">
            <div class="pool">
                <div class="pool-header flex items-center justify-center">
                    <h2>Pools</h2>
                </div>
                <div class="pool-body">
                    <div class="items">
                        <div class="item mb-3" v-for="(item, index) in items" :key="index">
                            <h2 class="name mb-3">{{ item.name }}</h2>
                            <div class="row flex">
                                Assets
                                <div class="value ml-auto">
                                    {{ item.assets }}
                                </div>
                            </div>
                            <div class="row flex mt-1">
                                Total Liquidity
                                <div class="value ml-auto">
                                    {{ item.totalLiquidity }}
                                </div>
                            </div>
                            <div class="row flex mt-1">
                                APY
                                <div class="value ml-auto">
                                    {{ item.apy }}
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
    name: 'pool',

    layout: 'app',

    data() {
        return {
            items: [
                {
                    name: 'Optimisation Pool',
                    assets: 'EURO-L',
                    totalLiquidity: '$0',
                    apy: '0%',
                },
                {
                    name: 'Stability Pool',
                    assets: 'BTCB, XUAH, anyBTC, BRZ',
                    totalLiquidity: '$0',
                    apy: '0%',
                },
                {
                    name: 'Arbitrage Pool',
                    assets: 'ETH, USDC, EURO-L',
                    totalLiquidity: '$0',
                    apy: '0%',
                }
            ]
        }
    }
}
</script>

<style lang="scss">
    .pool-wrapper {
        color: #fff;
        padding: 50px 0;

        .pool {
            background: #11102D;
            box-shadow: 20px 4px 40px rgba(22, 23, 49, 0.15);
            border-radius: 20px;
            padding: 37px 46px;
            min-width: 539px;

            .pool-header {
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

            .pool-body {
                .items {
                    .item {
                        background: #1F1E3C;
                        border-radius: 15px;
                        padding: 18px 23px;

                        .name {
                            font-size: 18px;
                            font-style: normal;
                            font-weight: 700;
                            line-height: 22px;
                            letter-spacing: 0em;
                            text-align: left;

                        }

                        .row {
                            font-size: 14px;
                            font-style: normal;
                            font-weight: 400;
                            line-height: 17px;
                            letter-spacing: 0em;
                            text-align: left;
                            color: #A6A0BB;

                            .value {
                                color: #fff;
                            }
                        }
                    }
                }
            }
        }
    }

    @media (max-width: 768px) {
        .pool-wrapper {
            .pool {
                width: calc(100vw - 30px);
                min-width: unset;
                padding: 30px 25px;
            }
        }
    }
</style>