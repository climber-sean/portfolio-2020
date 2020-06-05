<template>
  <div class="home-container">
    <div :class="{'fade-in': entering}" ref="hero" class="top-half" @mousemove="moveHero" @mouseleave="removeMoveClass">
      <div class="container">
        <div :class="{shrink: entering, grow: leaving}" ref="title-container" class="title-container">
          <h1 ref="title">Sean Butlin <span>Frontend Developer</span></h1>
          <nuxt-link to="/work" title="Work" class="btn-ghost">My Work</nuxt-link>
        </div>
      </div>
    </div>
    <div :class="{rotate: entering}" class="social-bar" ref="social-bar">
      <a href="https://www.linkedin.com/in/sean-butlin-73307a16a/" title="LinkedIn" target="_blank">
        <font-awesome-icon class="social-bar__icons" :icon="['fab', 'linkedin']"/>
      </a>
      <a href="https://github.com/climber-sean" title="GitHub" target="_blank">
        <font-awesome-icon class="social-bar__icons" :icon="['fab', 'github']"/>
      </a>
      <a href="" @click.prevent="contactForm" title="Contact me">
        <font-awesome-icon class="social-bar__icons" :icon="['fas', 'envelope']"/>
      </a>
    </div>
    <div class="bottom-half">
      <div :class="{'fade-in': entering}" ref="about" class="container">
        <h2>About Me</h2>
        <p>Frontend Developer based in Staffordshire with a strong passion for all things technology. I have experience building fully responsive sites for the web with a good knowledge of HTML, CSS, JavaScript and much more including CSS pre-processors and the latest JavaScript frameworks. For the past 2 years I have been working within the automotive industry creating websites for car dealerships all across the UK with a focus on clean design, semantic code and a great user experience. Get in touch if you would like to work together or have an opportunity you think I could be interested in. </p>
        <h2>Skills</h2>
        <ul class="skills-list">
          <li class="skills-list__item">HTML5</li>
          <li class="skills-list__item">CSS3</li>
          <li class="skills-list__item">BEM</li>
          <li class="skills-list__item">Less</li>
          <li class="skills-list__item">Sass</li>
          <li class="skills-list__item">Bootstrap</li>
          <li class="skills-list__item">JavaScript</li>
          <li class="skills-list__item">jQuery</li>
          <li class="skills-list__item">Vue.js</li>
          <li class="skills-list__item">Nuxt</li>
          <li class="skills-list__item">React</li>
          <li class="skills-list__item">API integration</li>
          <li class="skills-list__item">Git</li>
          <li class="skills-list__item">Photoshop</li>
          <li class="skills-list__item">Illustrator</li>
        </ul>
      </div>
    </div>
    <app-footer></app-footer>
  </div>
</template>

<script>
import Footer from '@/components/footer.vue';

export default {
  mounted() {
    this.entering = true;
  },
  beforeDestroy() {
   this.$refs["title-container"].classList.add('grow');
   this.$refs["about"].classList.add('grow');
   this.$refs["social-bar"].classList.add('leave');
  },
  components: {
    appFooter: Footer
  },
  data() {
    return {
      entering: false,
      leaving: false
    }
  },
  methods: {
    contactForm() {
      $nuxt.$emit('useContact');
    },
    moveHero() {
      var hero = document.querySelector('.top-half');
      var heroInfo = hero.getBoundingClientRect();
      var topHalf = Math.floor(heroInfo.height / 2);
      var leftHalf = Math.floor(heroInfo.width / 2);
      if (event.clientY < topHalf) {
        hero.classList.remove('move-down');
        hero.classList.add('move-up');
      }
      if (event.clientY > topHalf) {
        hero.classList.remove('move-up');
        hero.classList.add('move-down');
      }
      if (event.clientX > leftHalf) {
        hero.classList.remove('move-right');
        hero.classList.add('move-left');
      }
      if (event.clientX < leftHalf) {
        hero.classList.remove('move-left');
        hero.classList.add('move-right');
      }
    },
    removeMoveClass() {
      var hero = document.querySelector('.top-half');
      hero.classList.remove('move-up');
      hero.classList.remove('move-down');
      hero.classList.remove('move-right');
      hero.classList.remove('move-left');
    }
  }
}
</script>

<style lang="scss">
@import '~assets/variables.scss';

.home-container {
  position: relative;
  overflow-x: hidden;
}

.social-bar {
  position: absolute;
  width: 200px;
  left: calc(50% - 100px);
  top: calc(60vh - 30px);
  height: 60px;
  background: $secondary-colour;
  display: flex;
  justify-content: center;
  align-items: center;
  border-radius: 3px;
  box-shadow: 0 0 12px 5px rgba(0,0,0,0.2);
  opacity: 0;

  @media handheld, only screen and (max-width: $laptop) {
    top: calc(50vh - 30px);
  }

  @media handheld, only screen and (max-width: $mobile) {
    top: calc(100vh - 45px);
  }

  &.rotate {
    animation: fade-in 0.5s 0.25s ease-in forwards;
  }

  &.leave {
    animation: fade-out 0.5s ease-out forwards !important;
  }

  &__icons {
    color: white;
    margin: 0 8px;
    font-size: 28px;
    transition: all 0.2s ease-in-out;

    &:hover {
      transform: scale(1.3);
      color: $primary-colour;
    }
  }
}

.container {
  max-width: 1280px;
  margin: 0 auto;
}

.top-half,
.bottom-half {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.top-half.move-up {
  &:before {
    top: -20%;
    transition: all 2s ease-out;
  }
}

.top-half.move-down {
  &:before {
    top: 0;
    transition: all 2s ease-out;
  }
}

.top-half.move-left {
  &:before {
    left: 0;
    transition: all 4s ease-out;
  }
}

.top-half.move-right {
  &:before {
    left: -20%;
    transition: all 4s ease-out;
  }
}

.top-half {
  height: 60vh;
  background: $gradient-bg-hero;
  position: relative;
  overflow:hidden;
  @media handheld, only screen and (max-width: $laptop) {
    height: 50vh;
  }
  @media handheld, only screen and (max-width: $mobile) {
    height: 100vh;
  }
  &:before {
    display: block;
    content: url('~assets/hero-overlay.svg');
    position: absolute;
    top: -10%;
    left: -10%;
    z-index: 0;
    transition: all 1s ease-out;
    width: 120%;
    height: 120%;
    opacity: 0.3;
    @media handheld, only screen and (max-width: $tablet) {
      // Makes sure background SVG on top half fits across all tablet devices
      width: 170%;
    }
    @media handheld, only screen and (max-width: $mobile) {
      content: url('~assets/hero-overlay-mobile.svg');
    }
  }
  .title-container {
    opacity: 0;
    position: relative;
    z-index: 1;
    &.shrink {
      animation: shrink-fade-in 0.75s ease-in forwards;
    }
    &.grow {
      animation: grow-fade-out 0.75s ease-out forwards;
    }
  }
  h1 {
    span {
      display: block;
      font-weight: 400;
      font-size: 22px;

      @media handheld, only screen and (max-width: $mobile) {
        font-size: 18px;
      }
    }
  }
}

.bottom-half {
  padding: 100px 0;
  background: $gradient-bg;
  color: darken(white,10%);

  @media handheld, only screen and (max-width: $mobile) {
    padding: 50px 0;
  }

  .container {
    opacity: 0;
    padding: 0 80px;

    &.grow {
      animation: grow-fade-out 0.75s ease-out forwards !important;
    }

    @media handheld, only screen and (max-width: $mobile) {
      padding: 40px 20px;
    }
  }

  .container.fade-in {
    animation: fade-in 0.75s 0.5s ease-in forwards;
  }
  
  p {
    margin-bottom: 50px;
  }

  .skills-list {
    margin: 0;
    padding: 0;
    display: flex;
    flex-wrap: wrap;
    list-style: none;

    &__item {
      box-sizing: border-box;
      flex: 0 0 calc(100% / 4 - 10px);
      margin: 5px;
      background: darken($primary-colour, 10%);
      padding: 5px;
      border-bottom: 5px solid $accent-colour2;

      @media handheld, only screen and (max-width: $mobile) {
        flex: 0 0 calc(100% / 2 - 10px);
      }
    }
  }
}
</style>
