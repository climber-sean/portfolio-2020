<template>
  <div class="home-container">
    <div class="top-half" @mousemove="moveHero" @mouseleave="removeMoveClass">
      <div class="container">
        <div class="title-container">
          <h1>Sean Butlin <span>Frontend Developer</span></h1>
          <a href="" class="btn-ghost">My Work</a>
        </div>
      </div>
    </div>
    <div class="social-bar">
      <a href="">
        <font-awesome-icon class="social-bar__icons" :icon="['fab', 'linkedin']"/>
      </a>
      <a href="">
        <font-awesome-icon class="social-bar__icons" :icon="['fab', 'github']"/>
      </a>
      <a href="">
        <font-awesome-icon class="social-bar__icons" :icon="['fas', 'envelope']"/>
      </a>
    </div>
    <div class="bottom-half">
      <div class="container">
        <h2>About Me</h2>
        <p>Lorem, ipsum dolor sit amet consectetur adipisicing elit. Labore quis reprehenderit qui iste repudiandae praesentium! Quae, voluptatum quasi. Quo, consectetur veniam. Voluptate voluptatem eos velit ut voluptatibus obcaecati consequatur quis?</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  methods: {
    moveHero() {
      var hero = document.querySelector('.top-half');
      var heroInfo = hero.getBoundingClientRect();
      var topHalf = Math.floor(heroInfo.height / 2);
      var leftHalf = Math.floor(heroInfo.width / 2);
      console.log(event);
      if (event.clientY < topHalf) {
        hero.classList.remove('move-down');
        hero.classList.add('move-up');
      }
      if (event.clientY > topHalf) {
        hero.classList.remove('move-up');
        hero.classList.add('move-down');
      }
      if (event.clientX < leftHalf) {

      }
    },
    removeMoveClass() {
      var hero = document.querySelector('.top-half');
      hero.classList.remove('move-up');
      hero.classList.remove('move-down');
    }
  }
}
</script>

<style lang="scss">
@import '~assets/variables.scss';

.home-container {
  position: relative;
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
    top: -100px;
    transition: all 2s ease-out;
  }
}

.top-half.move-down {
  &:before {
    top: 0px;
    transition: all 2s ease-out;
  }
}

.top-half {
  height: 60vh;
  background: $bg-gradient;
  position: relative;
  overflow:hidden;
  &:before {
    display: block;
    content: url('~assets/hero-overlay.png');
    position: absolute;
    top: -50px;
    left: 0;
    z-index: 0;
    opacity: 0.12;
    transition: all 1s ease-out;
  }
  .title-container {
    position: relative;
    z-index: 1;
  }
  h1 {
    span {
      display: block;
      font-weight: 400;
      font-size: 22px;
    }
  }
}

.bottom-half {
  height: 40vh;
  background: $primary-colour;
  color: darken(white,10%);
}
</style>
