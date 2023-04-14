<template>
    <div ref="target">
        <Transition :name="animationType" appear>
            <div v-if="animate" class="animated-component">
                <Mouse />
                <slot />
            </div>
        </Transition>
    </div>
</template>

<script>
import { onMounted, onUnmounted, ref } from 'vue';
import { onIntersect } from '../composables/onIntersect';
import Mouse from './Mouse.vue';
export default {
    components: {
        Mouse
    },

    props: {
        animationType: {
            type: String,
            required: false,
            default: 'basic'
        }
    },
    setup() {
        const observer = ref();
        const target = ref();
        const animate = ref(false);
        onMounted(() => {
            observer.value = onIntersect(target.value, animate, false, { threshold: 0.3, });
        });
        onUnmounted(() => {
            document.addEventListener('load', () => observer.unobserve(target.value))     
        });
        return {
            animate,
            target
        };
    }
};
</script>

<style scoped>
.basic-enter-active,
.basic-leave-active {
    transition: transform 0.5s ease;
}

.basic-enter-from,
.basic-leave-to {
    transform: translateY(15px) skewX(5deg);
    opacity: 0;
}
</style>