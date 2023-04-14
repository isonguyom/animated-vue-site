<template>
    <main>
        <Mouse />
        <section class="no-page">
            <BasicTransition>
                <h1 class="block-title">No page</h1>
            </BasicTransition>
        </section>
    </main>
</template>

<script>
import Mouse from '../components/Mouse.vue';
import BasicTransition from '../components/BasicTransition.vue';

export default {
    components: { Mouse, BasicTransition }
}
</script>


<style scoped>
.no-page {
    background-color: #1b1b1b1c;
    min-height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
}
</style>