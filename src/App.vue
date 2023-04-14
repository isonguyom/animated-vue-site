<script setup>
import { RouterView } from 'vue-router'
import Loader from './components/Loader.vue';
import Navbar from './components/Navbar.vue';
import Mouse from "./components/Mouse.vue";
import { reactive } from "vue";



const state = reactive({ isLoading: false });
</script>

<template>
<div>
  <div v-if="state.isLoading">
    <Loader></Loader>
  </div>
  <div v-else class="wrapper">
    <Mouse></Mouse>
    <Navbar></Navbar>
    <Transition name="swap" appear mode="out-in">
    <RouterView />
    </Transition>
    <p class="copyright">©2019 Jomor Design - All rights reserved</p>
  </div>
</div>
</template>

<style scoped>
.wrapper {
  background-color: #ffffff04;
  width: 100%;
  overflow-x: hidden;
}

.wrapper::after { 
  content:'';
  position: fixed;
  z-index: -1;
  height: 140px;
  bottom: 3vh;
  right: 4%;
  width: 1px;
  background: #fff;
}

.wrapper::before { 
  content:'';
  position: fixed;
  z-index: 1;
  height: 20px;
  bottom: 3vh;
  right: 4%;
  width: 1px;
  background: #3b3b3b;
}
.copyright {
  font-size: 0.5rem;
  padding: 20px 4%;
  color: #ffffff69;
}

.swap-enter-active,
.swap-leave-active {
    transition: transform 0.5s ease;
}

.swap-enter-from,
.swap-leave-to {
    opacity: 0;
}

@media screen and (min-width: 767px) {
  .copyright {
    font-size: 0.7rem;
  }
}
</style>
