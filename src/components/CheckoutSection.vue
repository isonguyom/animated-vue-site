<template>
    <section class="block-wrapper">
        <BasicTransition>
            <h3 class="block-title">HEY!<br> I GOT A NEW SITE</h3>
            <p class="block-text">
                And just like every sequel, it’s not as good as the first one. <a href="">Check it out!</a>
                <img class="gif" src="/images/hey-gif.gif" alt="">
            </p>
        </BasicTransition>
    </section>
</template>
<script>
import BasicTransition from './BasicTransition.vue';

export default {
    components: { BasicTransition }
}
</script>

<style scoped>
section {
    padding: 30px 6%;
    min-height: 100vh;
}

.block-wrapper {
    display: flex;
    flex-direction: column;
    justify-content: center;
    padding-bottom: 250px;
}

.block-title {
    font-size: 13vw;
}

.block-text {
    font-size: 0.9rem;
}

.gif {
    z-index: -10;
    display: none;
    border-radius: 10px;
    position: absolute;
    right: 4vw;
    top: -18vw;
    transform: rotate(-5deg);
}

@media screen and (min-width: 480px) {
    .block-title {
        line-height: 1em;
    }

    .block-text {
        font-size: 1.2rem;
    }
}

@media screen and (min-width: 768px) {
    .block-title {
        font-size: 8vw;
    }
}

@media screen and (min-width: 992px) {
    section {
        padding: 30px 10%;
    }

    .block-title {
        font-size: 7.5vw;
    }


    .block-text a:hover+.gif {
        display: block;
    }
}
</style>