<template>
    <div class="Loader">
        <div class="indicator">
            <hr>
        </div>
    </div>
</template>
  
  <!-- <script>
  export default {
    name: "Loader",
  };
  </script> -->
  
<style scoped>
.Loader {
    width: 100%;
    height: 100vh;
    background-color: #fff;
}

.indicator {
    width: 150px;
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translateX(-50%) translateY(-50%);
    text-align: center;
}

hr {
    display: block;
    border: 1px solid rgb(160, 158, 158);
    animation: loader 3s linear infinite;
}

@keyframes loader {
    0% {
        transform: scaleX(0);
        opacity: 0;
    }

    100% {
        transform: scaleX(100%);
        opacity: 1;
    }
}</style>