<template>
    <footer class="footer p-5 mt-auto">
        <div class="container mx-auto flex justify-between items-center">
            <a href="#">
                <img src="~/assets/logo-v2.svg" alt="logo" />
            </a>
            <div class="navs">
                <router-link to="/" class="nav">Home</router-link>
                <router-link to="/app" class="nav">App</router-link>
                <router-link to="/info" class="nav">Info</router-link>
                <router-link to="/listing" class="nav">Listing</router-link>
            </div>
            <div class="socials flex">
                <a href="#" target="blank" class="social">
                    <img src="~/assets/facebook.svg" alt="">
                </a>
                <a href="#" target="blank" class="social">
                    <img src="~/assets/linkedin.svg" alt="">
                </a>
                <a href="#" target="blank" class="social">
                    <img src="~/assets/twitter.svg" alt="">
                </a>
                <a href="#" target="blank" class="social">
                    <img src="~/assets/instagram.svg" alt="">
                </a>
                <a href="#" target="blank" class="social">
                    <img src="~/assets/youtube.svg" alt="">
                </a>
            </div>
        </div>
    </footer>
</template>

<style lang="scss" scoped>
    .footer {
        background: #070423;
        color: #fff;
        margin-top: auto;

        .navs {
            .nav {
                margin-right: 25px;
            }
        }

        .socials {
            .social {
                margin-right: 15px;
                width: 22px;
                height: 22px;
            }
        }
    }

    @media (max-width: 768px) {
        .footer {
            .container {
                flex-direction: column;

                .navs {
                    margin: 15px 0;
                }
            }
        }
    }
</style>