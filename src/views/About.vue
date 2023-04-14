<template>
    <main>
        <Mouse />

        <section class="block-wrapper about-hero">
            <BasicTransition>
                <h3 class="block-title">NICE TO<br> MEET YOU</h3>
                <p class="block-text">I’m Jo and I’m here to assist you. My feeling is you already know how crucial it is
                    for
                    your
                    business to have a
                    robust <a href="">brand</a> and <a href="">website</a>. Why? Because you’re very smart. That’s why. The
                    good
                    news is: you came to the right place. I’m awesome at doing those things. True story.</p>
            </BasicTransition>
        </section>

        <section class="words-section">
            <BasicTransition>
            <h3 class="block-title">I KNOW WORDS <span>I HAVE THE BEST WORDS</span></h3>
            </BasicTransition>
            <h3 class="label">Word</h3>
            <div class="words-wrapper">
                <div v-for="(item, key) in words" :key="item.caption" class="word">
                    <BasicTransition>
                    <h3 class="caption">{{ item.caption }}</h3>
                    <p>{{ item.text }}</p>
                    </BasicTransition>
                </div>
            </div>
        </section>

        <section class="block-wrapper clients">
            <BasicTransition>
                <h3 class="block-title">78% OF MY CLIENTS SAY I’M A GENIUS</h3>
                <p class="block-text">The other 22% say I’m a <a href="">sexy genius.</a>
                    <img class="gif" src="/images/client-gif.gif" alt="">
                </p>
                <Button text="&nbsp;get&nbsp;in&nbsp;touch" color="#D76018" :size="size" :top="top" :right="right"></Button>
            </BasicTransition>
        </section>

        <Footer :title="'work'" :link="'work'"></Footer>
    </main>
</template>

<script>
import Footer from '../components/Footer.vue';
import Button from '../components/Button.vue';
import Mouse from '../components/Mouse.vue';
import BasicTransition from '../components/BasicTransition.vue';

export default {
    components: {
        Footer,
        Button,
        Mouse,
        BasicTransition
    },

    data() {
        return {
            words: [
                {
                    caption: 'HARD WORK',
                    text: 'Nothing worth having comes easy. That’s why I welcome the struggle and no matter what I try to accomplish, I always give 100%. Unless I give 80%. But what’s 20% really?'
                },
                {
                    caption: 'HEALTHY RELATIONSHIPS',
                    text: 'The relationship with my clients is one the most important things to me. I have nothing but respect for a client who is willing to trust me with the success of his/her business. Except for you David. You suck.'
                },
                {
                    caption: 'ORIGINALITY',
                    text: 'When it comes to obtaining and keeping your customers attention, originality is key. Thinking outside the box is important. Trust me. You don’t want to be another flavourless boring vanilla ice cream. You almost want to be too original. Looking at you Häagen-Dazs Vodka Key Lime Pie flavoured ice cream.'
                },
                {
                    caption: 'GOOD TIMES',
                    text: 'Work is great yes. But life isn’t all about work. I keep all my collaborations fun, light and enjoyable by trying to be a decent human being and treat others with respect. I know, right? It’s like I cracked the code.'
                },
                {
                    caption: 'AUTHENTICITY',
                    text: 'Takin’ chances while we dancin’ in the party fo’ sho’. Slip my hoe a forty-fo’ and she got in the back do’. Bitches lookin’ at me strange but you know I don’t care. Step up in this motherfucker just a-swangin my hair.'
                },
                {
                    caption: 'QUINTESSENTIAL“ISM”',
                    text: 'How awesome is this word honestly? It belongs here because I continually deliver quality product and services so yeah. Quintessential“ism” stays.'
                },
            ],

            top: '60vh',
            right: '35vw',
            size: '110px',
        }
    },

    methods: {
        onResize() {
            console.log(window.innerWidth)

            if (window.innerWidth <= 479) {
                this.size = '110px',
                    this.top = '60vh'
            }
            if (window.innerWidth > 479) {
                this.top = '62vh',
                    this.right = '15vw',
                    this.size = '110px'
            }
            if (window.innerWidth > 767) {
                this.size = '148px',
                    this.right = '10vw'
                this.top = '50vh'
            }
            if (window.innerWidth > 991) {
                this.right = '40vw'
            }
        }
    },


    mounted() {
        this.onResize()
        window.addEventListener('resize', this.onResize)
    },

    unmounted() {
        window.removeEventListener('resize', this.onResize)
    },
}
</script>

<style scoped>
section {
    padding: 30px 6%;
}

.block-wrapper {
    display: flex;
    flex-direction: column;
    justify-content: center;
}

.about-hero {
    background: url('/images/Monocle-Logo.svg');
    background-repeat: no-repeat;
    background-position: 80% 75px;
    background-size: 250px;
    padding-top: 60px;
    padding-bottom: 18vw;
    justify-content: space-between;
    height: 133vh;
}


.about-hero p {
    width: 90%;
    font-size: 1rem;
    line-height: 2em;
}

.words-section {
    padding-top: 120px;
    padding-bottom: 80px;
    overflow-x: hidden;
}

.words-section .block-title {
    margin-bottom: 0;
}

.words-section .block-title span {
    color: transparent;
}

.words-wrapper {
    padding: 90px 0;
}

.label {
    color: transparent;
    -webkit-text-stroke: 1px #ffffff25;
    position: absolute;
    font-size: 28vw;
    transform: translate(45vw, 320px) rotate(90deg);
    font-weight: 900;
    text-transform: uppercase;
    text-align: right;
}

.word {
    margin-bottom: 70px;
    padding-right: 10%;
}

.word:last-child {
    margin-bottom: 0;
}

.word p {
    opacity: 0.6;
    line-height: 1.8em;
    margin-top: 15px;
    font-weight: 300;
    font-size: 0.8rem;
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

.clients {
    padding-bottom: 280px;
}


@media screen and (min-width: 480px) {
    .about-hero {
        background-position: right 40px;
        background-size: 55vw;
        padding-top: 300px;
        justify-content: center;
    }

    .about-hero p {
        margin-top: 50px;
        width: 80vw;
    }


    .words-section .block-title {
        font-size: 10vw;
    }

    .word .caption {
        font-size: 1.4rem;
    }

    .word p {
        width: 90%;
        line-height: 1.8em;
        font-size: 0.9rem;
    }
}

@media screen and (min-width: 768px) {
    .about-hero {
        background-position: 85% 60px;
        background-size: 420px;
        padding-top: 100px;
        padding-bottom: 70px;
        justify-content: space-around;
    }

    .about-hero .block-title {
        margin-bottom: 10vw;
    }

    .about-hero .block-text {
        width: 63%;
        font-size: 1.2rem;
    }

    .words-section .block-title {
        width: 80%;
        font-size: 8.5vw;
    }

    .words-section .label {
        transform: translate(45vw, 0) rotate(90deg);
    }

    .words-wrapper {
        display: flex;
        flex-wrap: wrap;
        justify-content: space-between;
        margin-top: 60px;
    }

    .word {
        width: 50%;
    }
}

@media screen and (min-width: 992px) {
    section {
        padding: 30px 10%;
    }

    .about-hero {
        background-position: 85% 50px;
        background-size: 55vh;
        height: 100vh;

    }

    .about-hero .block-title {
        margin-bottom: 30px;
    }

    .about-hero .block-text {
        width: 50%;
        font-size: 1.4rem;
    }

    .words-section {
        padding-top: 230px;
        padding-bottom: 100px;
    }

    .words-section .block-title {
        width: 100%;
        font-size: 6vw;
        margin-bottom: 80px;
    }

    .words-section .label {
        font-size: 20vw;
        transform: translate(55vw, 0) rotate(90deg);
    }

    .word p {
        width: 100%;
    }

    .block-text a:hover+.gif {
        display: block;
    }

}
</style>