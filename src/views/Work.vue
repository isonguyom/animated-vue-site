<template>
    <main>
        <Mouse></Mouse>

        <section class="block-wrapper work-hero">
            <BasicTransition>
                <h1 class="block-title">
                    I SOMETIMES DO GREAT WORK <span>OTHER TIMES I DO MEDIOCRE PUSH-UPS</span>
                </h1>
            </BasicTransition>
        </section>

        <section class="projects-section">
            <h3 class="label">Work</h3>
            <div class="projects-wrapper">
                <a href="" class="project" :style="{ backgroundImage: 'url(' + `images/${project.image}` + ')' }"
                    v-for="(project, key) in projects" :key="project.name">
                    <p class="project-year">{{ project.year }}</p>
                    <BasicTransition>
                        <p class="project-name">{{ project.name }}</p>
                        <p class="project-type">{{ project.type }}</p>
                    </BasicTransition>
                    <Button class="view-btn" text="view" :color="project.color" :bg-color="project.color" size="90px"
                        letterSpacing="1px" position="fixed"></Button>

                </a>
            </div>
        </section>
        <CheckoutSection></CheckoutSection>
        <Footer :title="'contact'" :link="'contact'"></Footer>
    </main>
</template>

<script>
import Footer from '../components/Footer.vue';
import Button from '../components/Button.vue';
import CheckoutSection from '../components/CheckoutSection.vue';
import Mouse from '../components/Mouse.vue';
import BasicTransition from '../components/BasicTransition.vue';

export default {
    components: { Footer, Button, CheckoutSection, Mouse, BasicTransition },

    data() {
        return {
            projects: [
                { name: '007 × SPYSCAPE', type: 'Website', year: '2020', image: 'project-img1.jpg', color: '#832515' },
                { name: 'Northand', type: 'Website', year: '2019', image: 'project-img2.jpg', color: '#FFE527' },
                { name: 'Kopema', type: 'Identity + Website', year: '2019', image: 'project-img3.jpg', color: '#5B946B' },
                { name: 'Chiro Actif', type: 'Identity', year: '2015', image: 'project-img4.jpg', color: '#E4002B' },
                { name: 'Le Vermeil', type: 'Identity + Website', year: '2018', image: 'project-img5.jpg', color: '#9D8B3F' },
                { name: 'Gymnase', type: 'Website', year: '2018', image: 'project-img6.jpg', color: '#44FFC5' },
                { name: 'O Point', type: 'Identity + Website', year: '2017', image: 'project-img7.jpg', color: '#12E09B' },
                { name: 'Le Royaume', type: 'Website', year: '2018', image: 'project-img8.jpg', color: '#AE1C20' },
                { name: 'Kare', type: 'Identity', year: '2015', image: 'project-img9.jpg', color: '#1b1b1b' },
            ]
        }
    }
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

.work-hero {
    min-height: 100vh;
    flex-direction: row;
    padding-top: 20vw;
}

.work-hero .block-title {
    font-size: 12.3vw;
}

.work-hero .block-title span {
    color: transparent;
}

.projects-section {
    padding-top: 70px;
    padding-bottom: 100px;
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

.project {
    background-size: cover;
    height: 60vw;
    width: 75%;
    display: flex;
    flex-direction: column;
    justify-content: end;
    padding: 10px;
    margin-bottom: 70px;
    cursor: none;
    text-decoration: none;
}

.project .project-name,
.project .project-type {
    text-transform: uppercase;
    padding: 12px 20px;
    width: fit-content;
    background-color: #fff;
    color: rgb(46, 45, 45);
    margin-bottom: 5px;
    cursor: none;
}

.project .project-type {
    font-size: 0.8rem;
}

.project .project-year {
    transform: translate(37.5vw, 45vw) rotate(90deg);
    font-size: 1.2rem;
    color: #fff;
    cursor: none;
}

.project .view-btn {
    display: none;
    top: 0;
    left: 30px;
}


@media screen and (min-width: 480px) {
    .work-hero {
        padding-top: 15vw;
    }

    .project {
        height: 50vw;
        width: 70vw;
        padding: 1.3em;
    }

    .project .project-name {
        font-size: 1.8rem;
        padding: 15px 30px;
    }

    .project .project-type {
        font-size: 1rem;
        padding: 15px 30px;
    }

    .project .project-year {
        transform: translate(35vw, 42vw) rotate(90deg);
    }
}


@media screen and (min-width: 768px) {
    .work-hero {
        flex-direction: column;
        justify-content: center;
        align-items: center;
        padding: 80px 4%;

    }

    .work-hero .block-title {
        margin-bottom: 0;
        font-size: 12vw;
    }

    .projects-section {
        padding-top: 150px;
        padding-bottom: 150px;
    }

    .label {
        transform: translate(45vw, 0) rotate(90deg);
    }

    .project .project-year {
        transform: translate(35vw, 38vw) rotate(90deg);
    }
}

@media screen and (min-width: 992px) {
    section {
        padding: 30px 10%;

    }

    .work-hero {
        padding: 50px 3%;
    }

    .work-hero .block-title {
        font-size: 10vw;
    }

    .projects-section {
        padding-bottom: 180px;
    }

    .label {
        font-size: 20vw;
        transform: translate(55vw, 0) rotate(90deg);
    }


    .projects-wrapper {
        display: flex;
        justify-content: space-between;
        flex-wrap: wrap;
    }

    .project {
        height: 28vw;
        width: 45%;
        padding: 1.3em;
        margin-bottom: 150px;
    }

    .project:nth-child(even) {
        transform: translateY(10vw);
    }

    .project .project-year {
        transform: translate(18vw, 22vw) rotate(90deg);
        font-size: 1.3rem;
    }

    .project:nth-child(even) .view-btn {
        display: none;
        top: -130px;
        left: -650px;
    }
}
</style>