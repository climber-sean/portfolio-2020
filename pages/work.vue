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
    data() {
        return {
            projects: {
                portfolio: {
                    name: 'Portfolio',
                    description: 'This portfolio site you are currently on, built on the Nuxt framework',
                    skills: ['HTML','SCSS','Nuxt.js'],
                    thumbnail: 'ddd'
                }
            }
        }
    }
}
</script>

<style lang="scss">
.blank-div {
    height: 100vh;
    background: black;
}
</style>