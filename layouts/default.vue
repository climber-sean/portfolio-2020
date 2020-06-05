<template>
  <div class="layout-container">
    <app-nav ref="nav" />
    <nuxt :class="{'overlay-blur': contact}" />
    <transition name="slide-in">
    <app-contact v-if="contact" @close="contact = !contact"></app-contact>
    </transition>
  </div>
</template>

<script>
import SiteNav from "@/components/navigation.vue";
import Contact from "@/components/contact.vue";

export default {
  data() {
    return {
      contact: false
    }
  },
  created() {
    this.$nuxt.$on('useContact', () => {
        this.contact = !this.contact;
    })
  },
  components: {
    appNav: SiteNav,
    appContact: Contact
  },
}
</script>

<style lang="scss">

.layout-container {
  position: relative;
}

html {
  font-family: Arial, sans-serif;
  font-size: 16px;
  word-spacing: 1px;
  -ms-text-size-adjust: 100%;
  -webkit-text-size-adjust: 100%;
  -moz-osx-font-smoothing: grayscale;
  -webkit-font-smoothing: antialiased;
  box-sizing: border-box;
  background: black;
}

*,
*:before,
*:after {
  box-sizing: border-box;
  margin: 0;
}

.btn-ghost {
  padding: 12px 32px;
  color: white;
  text-decoration: none;
  border: 1px solid white;
  display: inline-block;
  text-transform: uppercase;
  margin: 15px 0;
  font-weight: 600;
  transition: ease-out 0.3s;

  &:hover {
    background: white;
    color: #2e3442;
  }

}

.overlay-blur {
  opacity: 0.1;
}
</style>
