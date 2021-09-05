<template>
    <div class="settings flex justify-center items-center" :class="{ show: isShow }">
        <div class="overlay" @click.prevent="onClickClose"></div>
        <div class="popup">
            <div class="header flex justify-between mb-10">
                <h2>Settings</h2>
                <a href="#" class="close-btn" @click.prevent="onClickClose">
                    <img src="~/assets/close-btn.svg" alt="">
                </a>
            </div>
            <div class="body">
                Max Price Impact
                <price-selector v-model="price" />
                <p>Always include decimal wrapped takens in list?</p>
                <div class="mt-3">
                    <toggle-button
                        v-model="alwaysInclude"
                        :width="52"
                        :height="30"
                        :margin="4.7"
                        :color="{ checked: '#1F1E3B', unchecked: '#1F1E3B' }"
                        :switch-color="{ checked: 'linear-gradient(90deg, #C734F7 0.35%, #8C72DA 57.62%, #7890D3 99.2%)', unchecked: '#A6A0BB'}" />
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import { ToggleButton } from 'vue-js-toggle-button'
import PriceSelector from '~/components/PriceSelector'

export default {
    name: "Settings",

    components: {
        PriceSelector,
        ToggleButton
    },

    props: [
        'value',
    ],

    data() {
        return {
            isShow: this.value,
            price: 2.0,
            alwaysInclude: false,
        }
    },

    methods: {
        onClickClose() {
            this.$emit('close')
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
    .settings {
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

            .body {
                p {
                    font-size: 14px;
                    font-style: italic;
                    font-weight: 500;
                    line-height: 17px;
                    letter-spacing: 0em;
                    text-align: left;
                }
            }
        }
    }

    @media (max-width: 768px) {
        .settings .popup {
            min-width: unset;
            width: calc(100vw - 30px);
            height: calc(100vh - 30px);
            padding: 30px 25px;
        }
    }
</style>