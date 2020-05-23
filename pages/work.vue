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
    }
}
</script>

<style lang="scss">
.blank-div {
    height: 100vh;
    background: black;
}
</style>