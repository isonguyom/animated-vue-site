<template>
  <main>
    <Mouse />
    
      <section class="home-hero block-wrapper">
        <div>
          <BasicTransition>
          <h3 class="block-title">I HELP BUSINESSES STAND OUT</h3>
          <p class="block-text">By creating <a class="hero-link1" href="">badass visual identities</a>
            <img class="gif gif1" src="/images/home-hero-gif1.gif" alt=""> and <a class="hero-link2" href="">awesome
              websites.</a>
            <img class="gif gif2" src="/images/home-hero-gif2.gif" alt="">
          </p>
          </BasicTransition>
        </div>
        <div class="hero-extra">
          <BasicTransition>
          <p class="extra-text">
            You can <span>scroll</span> if you want to, you can leave your friends behind
            ’Cause your friends don't <span>scroll</span> and if they don't <span>scroll</span>
            Well they're no friends of mine.
          </p>
          </BasicTransition>
        </div>
      </section>
    <section class="home-works">

      <div class="work-wrapper" v-for="(item, key) in works" :key="item.id">
        <h3 class="work-id">{{ item.id }}</h3>
        <BasicTransition>
        <h3 class="block-title">{{ item.name }}</h3>
        </BasicTransition>
        <p class="block-text">{{ item.type }}</p>
        <img class="work-img" :src="`/images/${item.image}`" alt="">
        <Button text="&nbsp;View&nbsp;project" :size="size" :top="top" :right="right" :color="item.btnColor"></Button>
      </div>
      <p class="label">featured work</p>
    </section>
    <CheckoutSection></CheckoutSection>
    <Footer :title="'Jo who?'" :link="'about'"></Footer>
  </main>
</template>

<script>
import Footer from '../components/Footer.vue';
import Button from '../components/Button.vue';
import CheckoutSection from '../components/CheckoutSection.vue';
import Mouse from '../components/Mouse.vue';
import BasicTransition from '../components/BasicTransition.vue';

export default {
  components: {
    Footer,
    Button,
    CheckoutSection,
    Mouse,
    BasicTransition
  },

  data() {
    return {
      top: '43vh',
      right: '10vw',
      size: '110px',
      works: [
        {
          id: '01',
          name: 'Opoint',
          type: 'Identity + Website',
          image: 'work-img1.jpg',
          btnColor: '#12E09B'
        },
        {
          id: '02',
          name: 'Spyscape',
          type: 'Website',
          image: 'work-img2.jpg',
          btnColor: '#832515'
        },
        {
          id: '03',
          name: 'Le Vermeil',
          type: 'Identity + Website',
          image: 'work-img3.jpg',
          btnColor: '#9D8B3F'
        },
        {
          id: '04',
          name: 'Chiro Actif',
          type: 'Identity',
          image: 'work-img4.jpg',
          btnColor: '#E4002B'
        },
        {
          id: '05',
          name: 'Northand',
          type: 'Website',
          image: 'work-img5.jpg',
          btnColor: '#FFE527'
        },
      ]
    }
  },

  methods: {
    onResize() {
      console.log(window.innerWidth)

      if (window.innerWidth <= 479) {
        this.size = '110px'
        this.top = '43vh'
      }
      if (window.innerWidth > 479) {
        this.top = '55vh',
          this.right = '15vw'
        this.size = '110px'
      }
      if (window.innerWidth > 767) {
        this.size = '148px'
        this.right = '8vw'
      }
      if (window.innerWidth > 991) {
        this.right = '10vw'
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
  min-height: 100vh;
}

.block-wrapper {
  display: flex;
  flex-direction: column;
  justify-content: center;
}

.block-title {
  font-size: 13vw;
}

.block-text {
  font-size: 0.9rem;
}

.home-hero {
  justify-content: space-around;
  min-height: 100vh;
}

.home-hero .block-title {
  line-height: 1.1em;
  margin-bottom: 40px;
}
.gif {
  display: none;
  z-index: -10;
  position: absolute;
  width: 75%;
  height: 35vw;
  transform: rotate(-5deg);
}

.gif1 {
  right: -20vw;
  top: -25vw;
  transform: rotate(-4deg);
}

.gif2 {
  border-radius: 10px;
  right: -4vw;
  top: -14vw;
  transform: rotate(4deg);
}

.hero-extra {
  color: #ffffff52;
  line-height: 1.3em;
  font-size: 0.6rem;
  max-width: 300px;
}

.hero-extra span {
  color: #fff;
}

.home-works {
  padding: 140px 0 79px;
}

.home-works .label {
  background-color: #fff;
  color: rgb(46, 45, 45);
  text-transform: uppercase;
  position: absolute;
  bottom: 0;
  width: fit-content;
  padding: 30px 40px;
  position: fixed;
}

.work-wrapper {
  min-height: 100vh;
}


.home-works .work-id {
  font-size: 30vw;
  color: transparent;
  -webkit-text-stroke: 1px #ffffff25;
  position: absolute;
  left: 48%;
  top: -20vw;
}

.home-works .block-title {
  z-index: 1;
  transform: translate(-35vw, 29vw) rotate(-90deg);
  text-align: right;
  -webkit-text-stroke: 1px #fff;
  color: transparent;
}

.home-works .block-text {
  transform: translate(35vw, 35vw) rotate(90deg);
  color: #ffffffa8;
  text-transform: uppercase;
  letter-spacing: 2px;
}

.home-works .work-img {
  height: 70vh;
  width: 75%;
  display: block;
  position: absolute;
  top: 0;
}

@media screen and (min-width: 480px) {
  .block-title {
    line-height: 1em;
  }

  .block-text {
    font-size: 1.2rem;
  }

  .home-hero {
    padding-top: 80px;
    padding-bottom: 20px;
    justify-content: space-between;
  }

  .hero-extra {
    line-height: 1.4em;
    font-size: 0.95rem;
    max-width: 450px;
  }

  .home-works {
    padding-top: 250px;
    padding-bottom: 200px;
  }

  .home-works .work-id {
    left: 70%;
    top: -14vw;
  }

  .home-works .block-title {
    transform: translate(5vw, -5vw) rotate(0deg);
    text-align: left;
  }

  .home-works .block-text {
    transform: translate(38vw, 50vw) rotate(90deg);
    font-size: 0.85rem;
  }


  .home-works .work-img {
    height: 80vh;
  }
}

@media screen and (min-width: 768px) {
  .block-title {
    font-size: 10vw;
  }


  .home-works .work-id {
    left: 0;
    top: 0;
    font-size: 20vw;
    transform: translate(83vw, 15vw) rotate(90deg);
  }

  .home-works .block-title {
    transform: translate(18vw, -5vw) rotate(0deg);
    font-size: 10.5vw;
  }

  .home-works .block-text {
    transform: translate(25vw, 40vw) rotate(90deg);
  }

  .home-works .work-img {
    width: 70%;
  }

}

@media screen and (min-width: 992px) {
  section {
    padding: 30px 10%;
  }

  .block-title {
    font-size: 7.5vw;
  }

  .home-hero {
    padding-top: 100px;
    padding-bottom: 30px;
  }

  .home-hero .hero-link1:hover+.gif1 {
    display: block;
  }

  .home-hero .hero-link2:hover+.gif2 {
    display: block;
  }

  .hero-extra {
    max-width: 430px;
    font-size: 0.9rem;
    line-height: 1.4em;
  }

  .work-wrapper {
    margin: 70px 0 0;
  }

  .home-works .work-id {
    transform: translate(82vw, 6vw) rotate(90deg);
  }

  .home-works .block-title {
    transform: translate(18vw, -4.5vw) rotate(0deg);
  }

  .home-works .block-text {
    transform: translate(19vw, 42vw) rotate(90deg);
  }

  .home-works .work-img {
    width: 65%;
  }
}
</style>
