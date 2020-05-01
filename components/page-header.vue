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
    background: $bg-gradient;
    display: flex;
    justify-content: center;
    align-items: center;
    overflow: hidden;
    position: relative;

    h1 {
        position: relative;
        z-index: 1;
    }

    &:before {
        display: block;
        position: absolute;
        top: 0;
        left: 0;
        content: url('~assets/hero-overlay.png');
        width: 100%;
        z-index: 0;
        opacity: 0.12;
    }
}

</style>