<template>
<header>
    <nav v-scroll="handleScroll">
        <nuxt-link to="/" title="Home">Home</nuxt-link>
        <nuxt-link to="/work" title="Work">Work</nuxt-link>
        <a @click="contactForm" title="Contact me">Contact</a>
    </nav>
</header>
</template>

<script>
import Contact from '@/components/contact.vue';

export default {
    methods: {
        handleScroll(evt, el) {
            console.log('scrolling');
            if(window.scrollY > el.offsetHeight) {
                el.classList.add('darken');
            };
            if(window.scrollY < el.offsetHeight) {
                el.classList.remove('darken');
            }
        },
        contactForm() {
            $nuxt.$emit('useContact');
        }
    },
    components: {
        appContact: Contact
    }
}
</script>

<style lang="scss">
@import '~assets/variables.scss';

nav {
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 20px 0;
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    z-index: 10;
    background: linear-gradient(180deg, rgba(0,0,0,0.5) 0%, rgba(55,71,96,0) 100%);
    transition: all 0.3s linear;

    &.darken {
        // background: rgba(0,0,0,0.6);
        background: lighten(black, 10%);
        box-shadow: 0 0 8px 4px rgba(0,0,0,0.2);
    }

    a {
        color: white;
        margin: 0 25px;
        text-decoration: none;
        text-transform: uppercase;
        letter-spacing: 4px;
        transition: all 0.2s linear;
        cursor: pointer;

        @media handheld, only screen and (max-width: $mobile) {
            margin: 0 15px;
            font-size: 14px;
        }
    }
}

</style>