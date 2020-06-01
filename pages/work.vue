<template>
<div>
    <app-page-header>
        Work
    </app-page-header>
    <div class="work-content">
        <div class="container">
            <ul class="projects">
                <app-work-item v-for="project in projects" 
                :name="project.name"
                :prog="project.progress" 
                :desc="project.desc" 
                :skills="project.skills" 
                :image="project.thumbnail"
                :git="project.git"
                :live="project.live">

                </app-work-item>
            </ul>
        </div>
    </div>
</div>
</template>

<script>
import PageHeader from '@/components/page-header.vue';
import WorkItem from '@/components/work-item.vue';

export default {
    components: {
        appPageHeader: PageHeader,
        appWorkItem: WorkItem
    },
    data() {
        return {
            projects: {
                portfolio: {
                    name: 'Portfolio',
                    desc: 'This portfolio site you are currently on, built to showcase my work and current projects ongoing. This site was built using the Nuxt framework which is based off Vue.',
                    skills: ['HTML','SCSS','Nuxt.js'],
                    thumbnail: '/portfolio-site.jpg',
                    git: 'https://github.com/climber-sean/portfolio-2020'
                },
                travelList: {
                    name: 'Travel List',
                    progress: true,
                    desc: 'Web application built in Vue.js that allows users to search for destinations or things to do, read reviews and add them to their bucket list. From their bucket list they can then keep track of when they visited a destination, and search hotels for that specific location',
                    skills: ['HTML', 'SCSS', 'Vue', 'Vuex', 'Axios', 'TripAdvisor API', 'Hotels API'],
                    thumbnail: '/travel-list.jpg',
                    git: 'https://github.com/climber-sean/travel-list'
                },
                inkfinity: {
                    name: 'Inkfinity Tattoo',
                    desc: 'Basic website with Couch CMS integrated built in 2018 for a local tattoo shop. The CMS allows the client to update their opening times, change homepage text and upload images to the gallery for each artist',
                    skills: ['HTML', 'LESS', 'JavaScript', 'Couch CMS'],
                    thumbnail: '/inkfinity.jpg',
                    live: 'http://www.inkfinitytattoostudio.co.uk'
                }
            }
        }
    }
}
</script>

<style lang="scss">
@import '~assets/variables.scss';

.projects {
    margin: 0 auto;
    padding: 0px;
}

.work-content {
    padding: 100px 0;
    background: $primary-colour;
}
</style>