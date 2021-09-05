<template>
    <div class="currency-dropdown">
        <div class="selected flex items-center" @click.prevent="onClickDropDrop">
            <span class="icon mr-2">
                <img :src="require(`~/assets/${value.icon}.svg`)" alt="">
            </span>
            {{ value.label }}
            <span class="ml-2">
                <i class="fas fa-chevron-down"></i>
            </span>
        </div>
        <select-token-pop-up 
            v-model="isShowPopUp" 
            @close="isShowPopUp = false" 
            @select="onSelectCurr" 
        />
    </div>
</template>

<script>
import SelectTokenPopUp from '~/components/popups/SelectToken'

export default {
    name: 'currency-dropdown',

    components: {
        SelectTokenPopUp
    },

    props: ['value'],

    data() {
        return {
            isShowPopUp: false,
        }
    },

    methods: {
        onClickDropDrop() {
            this.isShowPopUp = true;
        },
        onSelectCurr(curr) {
            this.$emit('input', curr)
        }
    },
}
</script>

<style lang="scss">
    .currency-dropdown {
        font-size: 16px;
        font-style: normal;
        font-weight: 500;
        line-height: 19px;
        letter-spacing: 0em;
        text-align: right;
        cursor: pointer;
    }
</style>