<template>
    <nav>
        <nuxt-link to="/">Home</nuxt-link>
        <nuxt-link to="/work">Work</nuxt-link>
        <nuxt-link to="/contact">Contact</nuxt-link>
    </nav>
</template>

<script>
export default {
    
}
</script>

<style lang="scss">
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

    a {
        color: white;
        margin: 0 25px;
        text-decoration: none;
        text-transform: uppercase;
        letter-spacing: 4px;
        transition: all 0.2s linear;

        &:hover {

        }
    }
}

</style>