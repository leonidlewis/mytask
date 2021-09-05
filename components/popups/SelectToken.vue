<template>
    <div class="select-token flex justify-center items-center" :class="{ show: isShow }">
        <div class="overlay" @click.prevent="onClickClose"></div>
        <div class="popup">
            <div class="header flex justify-between mb-10">
                <h2>Select Token</h2>
                <a href="#" class="close-btn" @click.prevent="onClickClose">
                    <img src="~/assets/close-btn.svg" alt="">
                </a>
            </div>
            <div class="body">
                <div class="search mb-5">
                    <input type="text" v-model="query" placeholder="Search for token" />
                    <a href="#" class="search-icon">
                        <img src="~/assets/Search.svg" alt="">
                    </a>
                </div>
                <div class="items flex flex-col">
                    <div class="item flex items-center" @click.prevent="onClickItem(index)" :class="{selected: index == selectedIndex}" v-for="(curr, index) in results" :key="index">
                        <div class="icon mr-3">
                            <img :src="require(`~/assets/${curr.icon}.svg`)" alt="">
                        </div>
                        <div class="label">
                            {{ curr.label }}
                            <p class="mute">
                                {{ curr.label }}
                            </p>
                        </div>
                        <div class="ballance ml-auto">
                            0.00 {{ curr.label }}
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import swapMixin from '~/mixins/swapMixin';

export default {
    name: 'select-token',

    props: ['value'],

    data() {
        return {
            isShow: this.value,
            query: '',
            selectedIndex: 0,
        }
    },

    mixins: [swapMixin],

    methods: {
        onClickClose() {
            this.$emit('close')
        },
        onClickItem(index) {
            this.selectedIndex = index
            this.$emit('select', this.currencies.find((item, indexCurr) => indexCurr === index))
        }
    },

    computed: {
        results() {
            if (this.query) {
                return this.currencies.filter(item => item.label.toLowerCase().includes(this.query.toLowerCase()))
            }
            return this.currencies
        }
    },

    watch: {
        value() {
            this.isShow = this.value
        }
    }
}
</script>

<style lang="scss">
    .select-token {
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
            }

            .search {
                background: #1F1E3B;
                border-radius: 43px;
                position: relative;
                padding: 10px;

                input {
                    width: 100%;
                    background: transparent;
                    color: #fff;
                    font-size: 16px;
                    border: none;
                    margin-left: 15px;
                    
                    ::placeholder {
                        color: #4A4970;
                    }

                    &:focus {
                        border: none;
                        outline: none;
                    }
                }

                .search-icon {
                    position: absolute;
                    top: 50%;
                    transform: translateY(-50%);
                    right: 15px;
                }
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

                    &.selected {
                        &:before {
                            content: '';
                            position: absolute;
                            top: 0; right: 0; bottom: 0; left: 0;
                            z-index: -1;
                            margin: -2px;
                            border-radius: inherit;
                            background: linear-gradient(90deg, #C734F7 0.35%, #8C72DA 57.62%, #7890D3 99.2%)
                        }
                    }

                    .label {
                        .mute {
                            font-size: 12px;
                            font-style: normal;
                            font-weight: 500;
                            line-height: 14px;
                            letter-spacing: 0em;
                            text-align: left;
                            color: #A6A0BB;
                        }
                    }

                    .ballance {
                        color: #A6A0BB;
                    }
                }
            }
        }
    }

    @media (max-width: 768px) {
        .select-token .popup {
            min-width: unset;
            width: calc(100vw - 30px);
            height: calc(100vh - 30px);
            padding: 30px 25px;
        }
    }
</style>