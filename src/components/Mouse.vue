<template>
    <div class="custom-cursor" v-if="show">
        <div id="cursor-big" class="cursor cursor-big"></div>
        <div id="cursor-small" class="cursor cursor-small"></div>
    </div>
</template>
  
<script>
export default {
    data() {
        return {
            show: false
        }
    },
    mounted() {
        this.show = true;
        const cursorBig = document.getElementById('cursor-big'),
            cursorSmall = document.getElementById('cursor-small'),
            // links = document.getElementsByTagName("a"),
            circularButton = document.getElementsByClassName("circular-button"),
            brandName = document.getElementsByClassName("brand-name"),
            navLink = document.getElementsByClassName("menu-item"),
            toggler = document.getElementsByClassName("menu-toggler"),
            footerText = document.getElementsByClassName("footer-text"),
            project = document.getElementsByClassName("project"),
            viewBtn = document.getElementsByClassName("view-btn"),

            menuItemsHover = [...navLink, ...toggler, ...footerText],
            circularButtonHover = [...circularButton, ...brandName],
            projectHover = [...project],
            viewBtnHover = [...viewBtn]

        // Event Listeners
        document.addEventListener("mousemove", onMouseMove);
        document.addEventListener("mouseenter", () => {
            cursorBig.style.opacity = 1;
            cursorSmall.style.opacity = 1;
        });
        document.addEventListener("mouseleave", () => {
            cursorBig.style.opacity = 0;
            cursorSmall.style.opacity = 0;
        });

        circularButtonHover.forEach((element) => {
            element.addEventListener("mouseover", onCircularButtonHover);
            element.addEventListener("mouseout", onCircularButtonHoverOut);
        });

        menuItemsHover.forEach((element) => {
            element.addEventListener("mouseover", onMenuItemHover);
            element.addEventListener("mouseout", onMenuItemHoverOut);
        })

        projectHover.forEach((element) => {
            element.addEventListener("mouseover", onProjectHover);
            element.addEventListener("mousemove", onProjectMove);
            element.addEventListener("mouseout", onProjectHoverOut);
        })

        // Event Handlers
        function onMouseMove(e) {
            cursorSmall.style.opacity = 1;
            cursorBig.style.transform = `translate3d(${e.clientX - 30}px, ${e.clientY - 30}px, 0)`;

            cursorSmall.style.transform = `translate3d(${e.clientX - 4}px, ${e.clientY - 4}px, 0)`;
        }
        function onCircularButtonHover() {
            cursorBig.style.display = 'none'
        }
        function onCircularButtonHoverOut() {
            cursorBig.style.display = 'block'
        }
        function onMenuItemHover() {
            cursorBig.style.backgroundColor = "#fff"
            cursorBig.style.width = "100px"
            cursorBig.style.height = "100px"
        }
        function onMenuItemHoverOut() {
            cursorBig.style.backgroundColor = "transparent"
            cursorBig.style.width = "70px"
            cursorBig.style.height = "70px"
        }
        function onProjectHover() {
            cursorBig.style.display = "none"
            viewBtnHover.forEach((element) => {
                viewBtnHover[projectHover.indexOf(this)].style.display = "block"
            })
        }
        function onProjectMove(e) {
            viewBtnHover.forEach((element) => {
                viewBtnHover[projectHover.indexOf(this)].style.transform = `translate3d(${e.clientX - 30}px, ${e.clientY - 130}px, 0)`;
            })
        }
        function onProjectHoverOut(e) {
            viewBtnHover.forEach((element) => {
                viewBtnHover[projectHover.indexOf(this)].style.display = "none"
            })
            cursorBig.style.display = "block"
            cursorBig.style.transform = `translate3d(${e.clientX - 30}px, ${e.clientY - 30}px, 0)`;
        }
    },

    // unmounted() {
    //     this.show = false
    // }
};
</script>
  
<style scoped>
.cursor {
    position: fixed;
    top: 0;
    left: 0;
    mix-blend-mode: difference;
    z-index: 99999;
    opacity: 0;
    pointer-events: none;
    transition: all 0.1s ease;
}

.cursor-big {
    width: 70px;
    height: 70px;
    border: 1px solid #ffffffb7;
    border-radius: 50%;
}

.cursor-small {
    width: 6px;
    height: 6px;
    background: transparent;
    border-radius: 50%;
}
</style>