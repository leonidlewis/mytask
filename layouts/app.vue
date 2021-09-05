<template>
    <div class="app">
        <header-bar @connect="onConnect" />
        <div class="content">
            <Nuxt />
        </div>
        <footer-bar />
        <connect-pop-up v-model="isShowConnect"  @close="isShowConnect = false" />
    </div>
</template>

<script>
import Footer from '~/components/Footer';
import Header from '~/components/Header';
import ConnectPopUp from '~/components/popups/Connect';

export default {
    components: {
        headerBar: Header,
        footerBar: Footer,
        connectPopUp: ConnectPopUp,
    },

    data() {
        return {
            isShowConnect: false,
        }
    },

    mounted() {
        this.$nuxt.$on('connect', this.onConnect)
    },

    methods: {
        onConnect() {
            this.isShowConnect = true
            
        }
    }
}
</script>

<style lang="scss">
    $bg: linear-gradient(113.51deg, #1C1647 19.16%, #1E1754 60.01%, #150C77 89.18%);

    .app {
        font-family: Poppins;
        height: 100vh;
        display: flex;
        flex-direction: column;
        background: $bg;

        .content {
            background: $bg;
        }
    }
</style>