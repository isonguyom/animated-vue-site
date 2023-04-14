<template>
    <router-link :to="{ name: link }" class="circular-button" :style="styleObject">
        <div class="btn-wrapper">
            <div class="text">{{ text }}</div>
        </div>
    </router-link>
</template>

<script>
export default {
    props: {
        text: String,
        color: String,
        size: {
            type: String,
            default: '120px'
        },
        top: {
            type: String,
            default: '0'
        },

        right: {
            type: String,
            default: '0'
        },
        link: {
            type: String,
            default: 'contact'
        },
        position: {
            type: String,
            default: 'absolute'
        },

        bgColor: {
            type: String,
            default: 'transparent'
        },

        letterSpacing: {
            type: String,
            default: '7px'
        },

        mobileText: {
            type: String,
            default: '#ffffffda'
        }
    },

    data() {
        return {
            hoverText: '#ffffffda'
        }
    },

    computed: {
        styleObject: function () {
            if (this.color === '#fff') {
                this.hoverText = '#1B1B1B'
            } else {
                this.hoverText = '#ffffffda'
            }
            return {
                '--color': this.color,
                '--size': this.size,
                '--hover-text': this.hoverText,
                '--top': this.top,
                '--right': this.right,
                '--text-color': this.mobileText,
                '--position': this.position,
                '--bg-color': this.bgColor,
                '--letter-spacing': this.letterSpacing
            }
        }
    }
}
</script>

<style scoped>
.circular-button {
    z-index: 2;
    color: var(--text-color) !important;
    position: var(--position);
    text-decoration: none;
    letter-spacing: 1px;
    text-transform: uppercase;
    text-shadow: 1px 1px 5px #525151;
    font-size: 0.55rem;
    font-weight: 500;
    text-align: center;
    border-radius: 50%;
    border: 2px solid var(--color);
    width: var(--size);
    height: var(--size);
    display: flex;
    align-items: center;
    justify-content: center;
    top: var(--top);
    right: var(--right);
    background-color: var(--color);
    cursor: none !important;
    transform: rotate(360deg);
    transition: all 0.7s ease;
    transition: transform 0.7s;
}

.circular-button .btn-wrapper {
    width: 100%;
    height: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
    cursor: none;
}

.circular-button .btn-wrapper .text {
    cursor: none;
    animation: round 10s ease-in-out -2s infinite forwards;
}

@keyframes round {

    100% {
        transform: rotate(360deg);
    }
}


@media screen and (min-width: 768px) {
    .circular-button {
        background-color: var(--bg-color);
        color: #ffffffda !important;
        font-size: 0.9rem;
        letter-spacing: var(--letter-spacing);
    }

    .circular-button:hover {
        background-color: var(--color);
    }


    .circular-button:hover .text {
        letter-spacing: 1px;
        color: var(--hover-text);
    }
}
</style>