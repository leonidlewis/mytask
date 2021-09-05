<template>
    <div class="header flex justify-between items-center">
        <router-link to="/" class="logo">
            <img src="~/assets/logo-v2.svg" alt="">
        </router-link>
        <div class="navs">
            <router-link to="/overview" class="nav">Overview</router-link>
            <router-link to="/swap" class="nav">Swap</router-link>
            <router-link to="/pools" class="nav">Pools</router-link>
            <router-link to="/roadmap" class="nav">Roadmap</router-link>
        </div>
        <a href="#" class="connect flex justify-center items-center" @click.prevent="onConnect">
            Connect
        </a>
        <a href="#" class="btn btn-bars" @click="onClickToggle">
           <i class="fas fa-bars"></i>
        </a>
        <div class="sidebar" :class="{ show: toggle }">
            <a href="#" class="close" @click.prevent="toggle = false">
                <i class="fas fa-times"></i>
            </a>
            <router-link to="/overview" class="nav">Overview</router-link>
            <router-link to="/swap" class="nav">Swap</router-link>
            <router-link to="/pools" class="nav">Pools</router-link>
            <router-link to="/roadmap" class="nav">Roadmap</router-link>
        </div>
    </div>
</template>

<script>
export default {
    name: 'navbar',

    data() {
        return {
            toggle: false,
        }
    },

    methods: {
        onClickToggle() {
            this.toggle = ! this.toggle
        },
        onConnect() {
            console.log('conectn');
            this.$emit('connect')
        },
    }
}
</script>

<style lang="scss" scoped>
    .header {
        width:90%;
        .navs {
           display: grid;
           grid-template-columns: 1fr 1fr 1fr 1fr;
           grid-gap: 40px;

           .nav {
               text-align: center;
           }
        }

        .connect {
            position: relative;
            color: #fff;
            margin-right: 25px;

          &:after {
                content: '';
                position: absolute;
                top: -60%;
                left: -60%;
                right: -60%;
                bottom: -60%;
                background-image: url(~/assets/connect-btn-border.svg);
                background-size: contain;
                background-position: center center;
                background-repeat: no-repeat;
          }
        }

        .btn-bars {
            font-size: 25px;
            display: none;
        }
    }

    .sidebar {
        position: fixed;
        z-index: 999;
        top: 0;
        bottom: 0;
        right: 0;
        width: 50vw;
        background-color: #000;
        padding: 30px;
        transform: translateX(100%);
        transition: all 0.3s;

        &.show {
            transform: translateX(0);
        }

        .close {
            position: absolute;
            font-size: 25px;
            top: 15px;
            right: 25px;
        }

        .nav {
            display: flex;
            flex-direction: column;
            margin-bottom: 15px;
        }
    }

    @media (max-width: 768px) {
        .header {
            .navs {
                display: none;
            }

            .connect {
                display: none;
            }


            .btn-bars {
                display: inline-block;
            }
        }
    }
</style>