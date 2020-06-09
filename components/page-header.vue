<template>
    <div class="page-header">
        <h1 class="title-container">
            <slot></slot>
        </h1>
    </div>
</template>

<script>
export default {
    
}
</script>

<style lang="scss">
@import "~assets/variables.scss";

.page-header {
    height: 300px;
    background: $gradient-bg-hero;
    display: flex;
    justify-content: center;
    align-items: center;
    overflow: hidden;
    position: relative;
    box-shadow: 0 0 12px 4px rgba(0,0,0,0.1);

    @media handheld, only screen and (max-width: $mobile) {
        height: 250px;
    }

    // I-phone landscape
    @media handheld, only screen and (min-device-width: 375px)
    and (max-device-width: 812px)
    and (orientation: landscape) {
        height: 200px;
    }

    h1 {
        position: relative;
        z-index: 1;
    }

    &:before {
        display: block;
        position: absolute;
        top: 0;
        left: 0;
        content: url('~assets/hero-overlay.svg');
        width: 100%;
        z-index: 0;
        opacity: 0.3;

        @media handheld, only screen and (max-width: $mobile) {
            content: url('~assets/hero-overlay-mobile.svg');
        }
    }
}

</style>