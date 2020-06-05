<template>
    <footer>
        <div class="social-links">
            <a href="https://www.linkedin.com/in/sean-butlin-73307a16a/" title="LinkedIn" target="_blank">
                <font-awesome-icon class="social-links__icons" aria-hidden="true" :icon="['fab', 'linkedin']"/>
            </a>
            <a href="https://github.com/climber-sean" title="GitHub" target="_blank">
                <font-awesome-icon class="social-links__icons" aria-hidden="true" :icon="['fab', 'github']"/>
            </a>
            <a @click.prevent="contactForm" title="Contact me">
                <font-awesome-icon class="social-links__icons" aria-hidden="true" :icon="['fas', 'envelope']"/>
            </a>
        </div>
        <div class="content">
            <p>Copyright &copy; 2020 Sean Butlin</p>
        </div>
    </footer>
</template>

<script>
export default {
    methods: {
        contactForm() {
            $nuxt.$emit('useContact');
        }
    }
}
</script>

<style lang="scss">
@import '~assets/variables.scss';

    footer {
        background-color: darken($primary-colour, 5%);
        padding: 15px 0;
        text-align: center;
        position: relative;
        overflow: hidden;
    }

    .social-links {
        a {
            text-decoration: none;
            color: white;
            font-size: 24px;
            margin: 0 5px;
            transition: all 0.2s linear;
            cursor: pointer;

            &:hover {
                color: $accent-colour2;
            }
        }
        margin: 5px 0;
    }
</style>