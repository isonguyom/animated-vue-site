<template>
    <nav class="Nav">
        <div class="menu-toggler" :class="{ active: menuActive }" @click="toggleMenu"></div>
        <Transition name="menu">
            <div class="menu-wrapper" v-if="menuActive">
                <Mouse />
                <router-link class="brand-name" :to="{ name: 'home' }" @click="toggleMenu">
                    <img src="/images/brand-image.svg" alt="Brand image">
                </router-link>

                <ul class="main-menu">
                    <li v-for="(item, key) in menuItem" :key="item.title">
                        <router-link class="menu-item" :to="{ name: item.link }" @click="toggleMenu">
                            <h3 class="link-title">{{ item.title }}</h3>
                            <p class="link-text">{{ item.text }}</p>
                        </router-link>
                    </li>
                </ul>
                <Button text="&nbsp;Start&nbsp;a&nbsp;Project" :color="color" mobileText="#1B1B1B" :size="size" :top="top"
                    :right="right" @click="toggleMenu"></Button>
                <footer>
                    <div>
                        <a v-for="(item, key) in contactDetails" :key="item.text" :href="item.href">{{ item.text }}</a>
                        <div class="social-links">
                            <a v-for="(link, key) in socialLinks" :key="link.alt" href=""><img
                                    :src="`images/${link.icon}.svg`" :alt="link.alt"></a>
                        </div>
                        <a class="translate" href="">FR — J’parle juste le Québecois</a>
                    </div>
                </footer>
            </div>
        </Transition>
    </nav>
</template>

<script>
import Button from './Button.vue';
import Mouse from './Mouse.vue';
export default {
    components: { Button, Mouse },
    data() {
        return {
            menuActive: false,
            top: '65vh',
            right: '4%',
            size: '120px',
            color: '#fff',
            menuItem: [
                { title: 'Work', text: 'All good stuff. Sorta', link: 'work' },
                { title: 'About', text: 'The man behind the beard', link: 'about' }
            ],
            contactDetails: [
                { href: 'mailto:mail@example.com', text: 'mail@example.com' },
                { href: 'tel:000-000-0000', text: '000-000-0000' }
            ],
            socialLinks: [
                { link: '#', icon: 'Social-Icon2', alt: 'facebook' },
                { link: '#', icon: 'Social-Icon1', alt: 'instagram' }
            ]
        }
    },

    methods: {
        toggleMenu() {
            this.menuActive = !this.menuActive
        },

        onResize() {
            if (window.innerWidth <= 479) {
                this.size = '120px'
            }
            if (window.innerWidth > 479) {
                this.size = '130px'
            }
            if (window.innerWidth > 767) {
                this.size = '175px'
            }
            if (window.innerWidth > 991) {
                this.top = '47vh',
                    this.right = '70%'
            }
        }
    },


    mounted() {
        window.addEventListener('load', this.onResize)
        window.addEventListener('resize', this.onResize)
    },

    unmounted() {
        window.removeEventListener('resize', this.onResize)
    },
}
</script>

<style scoped>
.Nav {
    width: 100%;
    z-index: 20;
}

.menu-toggler {
    z-index: 2;
    position: fixed;
    right: 4%;
    bottom: 3vh;
    color: #1B1B1B;
    background-color: #fff;
    border-radius: 50%;
    width: 46px;
    height: 46px;
    display: flex;
    justify-content: center;
    align-items: center;
    transition: all 250ms ease-out;
    cursor: none;
}


.menu-toggler:before,
.menu-toggler:after {
    content: '';
    width: 20px;
    height: 2px;
    border-radius: 50%;
    position: absolute;
    background: #1B1B1B;
    transition: transform 50ms ease-out;
    will-change: transform;
    cursor: none;
}

.menu-toggler:before {
    transform: translateY(-4px);
}

.menu-toggler:after {
    transform: translateY(4px);
}


.active.menu-toggler:before {
    transform: translateY(0) rotate(45deg);
}

.active.menu-toggler:after {
    transform: translateY(0) rotate(-45deg);
}

.menu-toggler:hover::after {
    transform: translateY(0);
}

.menu-toggler:hover::before {
    transform: translateY(0) rotate(90deg);
}

.menu-wrapper {
    color: #fff;
    background-color: #1B1B1B;
    width: 100%;
    min-height: 100vh;
    padding: 18px 6%;
    font-size: 0.8rem;
    position: fixed;
    top: 0;
    transition: all 1s ease-in-out;
}

.menu-wrapper>* {
    animation: menuItem 2s ease 1s both;
}

.menu-enter-active {
    animation: toggleMenu 3s ease;
}

.menu-leave-active {
    animation: toggleMenu 3s ease reverse;
}

.menu-enter-from,
.menu-leave-to {
    opacity: 0;
}

@keyframes toggleMenu {

    0% {
        opacity: 0;
    }

    50% {
        opacity: 1;
        background-color: #fff;
    }

    100% {
        opacity: 1;
        background-color: #1B1B1B;
    }
}

@keyframes menuItem {

    0% {
        opacity: 0;
        transform: translateY(30px) skewX(-10deg);
    }

    100% {
        opacity: 1;
    }
}

.menu-wrapper a {
    color: #fff;
    text-decoration: none;

}

.brand-name {
    background-color: #fff;
    display: block;
    width: 75px;
    height: 75px;
    border-radius: 50%;
    padding: 5px;
    cursor: none;
    transition: background-color 0.5s ease;
}

.brand-name img {
    cursor: none;
}

.brand-name:hover {
    background-color: #D86018;
}

.main-menu {
    list-style: none;
    text-align: right;
    float: right;
    margin-top: -15px;
}

.main-menu li {
    margin-top: -10px;
    margin-bottom: 45px;
    cursor: none;
}

.main-menu li:last-child {
    margin-bottom: 0;
}

.main-menu li a {
    display: block;
    transition: color 0.5s ease;
}

.main-menu .link-title {
    font-size: 16vw;
    font-weight: 900;
    -webkit-text-stroke: 1px #fff;
    color: transparent;
    cursor: none;
    transition: color 0.5s ease;
}

.main-menu .link-text {
    cursor: none;
}

.main-menu li a .link-title:hover {
    color: #fff;
}

.menu-wrapper footer {
    position: absolute;
    bottom: 0;
}

.menu-wrapper footer a {
    border-bottom: 1px solid gray;
    padding-bottom: 6px;
    display: block;
    width: fit-content;
    margin-bottom: 22px;
    cursor: pointer;
    transition: border-color 0.5s ease;
}

.menu-wrapper footer .social-links a {
    border-bottom: none;
    display: inline-block;
    margin-right: 15px;
    border: 1px solid #ffffff8a;
    border-radius: 50%;
    width: 30px;
    height: 30px;
}

.menu-wrapper footer .social-links a img {
    cursor: pointer;
}

.menu-wrapper footer .social-links a:last-child {
    margin-right: 0;
}

.menu-wrapper footer a.translate {
    font-weight: lighter;
    margin-top: 25px;
    color: #999797;
    border-color: #999797;
}

.menu-wrapper footer a:hover {
    border-color: #fff;
}

@media screen and (min-width: 480px) {
    .menu-toggler {
        width: 48px;
        height: 48px;
    }

    .menu-wrapper {
        padding-top: 28px;
    }

    .brand-name {
        width: 100px;
        height: 100px;
    }

    .main-menu {
        margin-top: -100px;
    }
}

@media screen and (min-width: 768px) {
    .menu-toggler {
        top: 38px;
        width: 58px;
        height: 58px;
    }

    .menu-wrapper {
        font-size: 1rem;
        padding-top: 33px;
    }

    .brand-name {
        width: 110px;
        height: 110px;
        padding: 5px;
        float: left;
    }

    .main-menu {
        margin-right: 9%;
        margin-top: 60px;

    }

    .main-menu .link-title {
        font-size: 12vw;
    }

    .menu-wrapper footer {
        clear: both;
        width: 100%;
        left: 0;
        padding-left: 9%;
        padding-right: 14%;
    }

    .menu-wrapper footer .social-links {
        float: left;
    }

    .menu-wrapper footer .social-links a {
        margin-bottom: 0;
    }

    .menu-wrapper footer a.translate {
        float: right;
        margin-top: 0;
    }
}

@media screen and (min-width: 992px) {
    .main-menu {
        margin-right: 9%;
        margin-top: 0;

    }

    .main-menu .link-title {
        font-size: 10vw;
    }

    .menu-wrapper footer {
        width: 100%;
        left: 0;
        padding-left: 6%;
        padding-right: 17%;
        padding-bottom: 5vh;
    }

    .menu-wrapper footer a {
        display: inline-block;
        margin-bottom: 0;
        margin-right: 40px;
    }

    .menu-wrapper footer a:last-child {
        margin-right: 0;
    }

    .menu-wrapper footer .social-links {
        position: absolute;
        width: 32px;
        height: 200px;
        right: -18%;
        top: -60px;
    }

    .menu-wrapper footer .social-links a {
        display: block;
        margin-bottom: 25px;
    }

    .menu-wrapper footer .social-links a:last-child {
        margin-bottom: 0;
    }
}
</style>