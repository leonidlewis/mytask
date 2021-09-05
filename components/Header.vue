<template>
    <div class="container mx-auto py-5">
        <div class="header flex justify-between items-center">
            <router-link to="/" class="logo">
                <img src="~/assets/logo-v2.svg" alt="">
            </router-link>
            <div class="navs ml-auto">
                <router-link to="/overview" class="nav">Overview</router-link>
                <router-link to="/swap" class="nav">Swap</router-link>
                <router-link to="/pools" class="nav">Pools</router-link>
                <router-link to="/roadmap" class="nav">Roadmap</router-link>
            </div>
            <a class="connect ml-auto flex justify-center items-center" @click.prevent="onConnect">
                Connect
            </a>
            <div class="sidebar" :class="{ show: toggle }">
                <a href="#" class="close" @click.prevent="toggle = false">
                    <i class="fas fa-times"></i>
                </a>
                <router-link to="/overview" @click.native="toggle = false" class="nav">Overview</router-link>
                <router-link to="/swap" @click.native="toggle = false" class="nav">Swap</router-link>
                <router-link to="/pools" @click.native="toggle = false" class="nav">Pools</router-link>
                <router-link to="/roadmap" @click.native="toggle = false" class="nav">Roadmap</router-link>
            </div>
            <a href="#" class="burger ml-10" @click.stop.prevent="onClickToggle" v-if="isDesktop">
                <img src="~/assets/burger.svg" alt="burger" />
            </a>
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

    mounted() {
        document.addEventListener('click', (e) => {
            const target = e.target
            if(target && ( ! target.closest('.sidebar') && ! target.classList.contains('burger'))) {
                this.toggle = false
            }
        }, false)
    },
    computed: {
        isDesktop(){
            if (window.innerWidth < 768) return true;
            return false;
        },
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
    .container{
        width: 90%;
    }
    .header {
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
            background: linear-gradient(90deg, #C734F7 0.35%, #8C72DA 57.62%, #7890D3 99.2%);
            box-shadow: 20px 4px 40px rgba(22, 23, 49, 0.15);
            border-radius: 112px;
            padding: 11px 35px;
            color: #fff;
            z-index: 2;

            font-size: 16px;
            font-style: normal;
            font-weight: 700;
            line-height: 19px;
            letter-spacing: 0em;
            text-align: center;

        }

        .btn-bars {
            font-size: 25px;
            display: none;
        }
    }

    .navs {
        .nav {
            color: #A6A0BB;
            position: relative;

            &.nuxt-link-active {
                color: #fff;

                &:after {
                    content: '';
                    width: 100%;
                    left: 0;
                    right: 0;
                    position: absolute;
                    bottom: -2px;
                    height: 2px;
                    background: #fff;
                }
            }
        }
    }

    .sidebar {
        position: fixed;
        z-index: 999;
        top: 0;
        bottom: 0;
        right: 0;
        width: 300px;
        background-color: #000;
        padding: 30px;
        transform: translateX(100%);
        transition: all 0.3s;
        color: #fff;

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

    @media (max-width: 1024px) {
        .container {
            padding-left: 25px;
            padding-right: 25px;
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