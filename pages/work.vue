<template>
<div>
    <app-page-header>
        Work
    </app-page-header>
    <div class="blank-div"></div>
</div>
</template>

<script>
import PageHeader from '@/components/page-header.vue';

export default {
    components: {
        appPageHeader: PageHeader
    },
    transition: {
        enter(el, done) {
            Velocity(el, { opacity: 1 }, { duration: 500, complete: done })
        },
        leave() {}
    }
}
</script>

<style lang="scss">
.blank-div {
    height: 100vh;
    background: black;
}
</style>