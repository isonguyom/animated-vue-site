<template>
    <section class="Footer">
        <BasicTransition>
            <h3 class="footer-text">
                <router-link :to="{ name: link }">
                    {{ title }}
                </router-link>
            </h3>
        </BasicTransition>
    </section>
</template>

<script>
import BasicTransition from './BasicTransition.vue';

export default {
    components: { BasicTransition },
    props: ['title', 'link']
}
</script>

<style scoped>
section {
    padding: 100px 0;
    display: flex;
    justify-content: center;
    align-items: center;
    min-height: 100vh;
}

section a {
    font-size: 20vw;
    text-transform: uppercase;
    border-bottom: 2px solid #fff;
    text-decoration: none;
    width: fit-content;
    color: transparent;
    -webkit-text-stroke: 1px #fff;
    transition: color 0.5s ease;
}

section a:hover {
    color: #fff;
}

@media screen and (min-width: 480px) {
    section a {
        font-size: 18vw;
    }
}

@media screen and (min-width: 768px) {
    section a {
        font-size: 12vw;
    }
}

@media screen and (min-width: 992px) {
    section a {
        font-size: 9.3vw;
    }
}
</style>