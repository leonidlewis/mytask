<template>
    <div class="max-price-impact">
        <div class="items">
            <div class="item" :class="{active:  index === selected}"
                @click.prevent="onSelect(index, percent)"
                 v-for="(percent, index) in percents" :key="index">
                {{ percent.label }}
            </div>
            <span class="item full">0<span class="percent">%</span></span>
        </div>
    </div>
</template>

<script>
export default {
    props: ['value'],

    data() {
        return {
            selected: 2,
            percents: [
                {
                    value: 0.5,
                    label: '0.5%',
                },
                {
                    value: 1.0,
                    label: '1.0%'
                },
                {
                    value: 2.0,
                    label: '2.0%'
                },
            ],
        }
    },

    mounted() {
        this.selected = this.getPercentIndexByValue(this.value)
    },

    methods: {
        getPercentIndexByValue(value) {
            return this.percents.findIndex(item => item.value === value)
        },
        onSelect(index, percent) {
            this.selected = index
            this.$emit('input', percent.value)
        }
    },

    watch: {
        value() {
            this.selected = this.getPercentIndexByValue(this.value)
        }
    },
}
</script>

<style lang="scss">
    .max-price-impact {
        .items {
            display: flex;
            margin: 15px 0;
            
            .item {
                margin-right: 6px;
                background: #1F1E3B;
                font-size: 16px;
                font-style: normal;
                font-weight: 500;
                line-height: 19px;
                letter-spacing: 0em;
                text-align: left;
                padding: 10px 17px;
                border-radius: 44px;
                cursor: pointer;
                transition: all .3s;
                text-align: center;

                &.full {
                    width: 100%;
                    color: #8E89D7;

                    .percent {
                        color: #fff;
                    }
                }

                &.active {
                    background: linear-gradient(90deg, #C734F7 0.35%, #8C72DA 57.62%, #7890D3 99.2%);
                }
            }
        }
    }
</style>