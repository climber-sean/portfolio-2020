<template>
<div>
    <app-page-header>
        Work
    </app-page-header>
    <div class="work-content">
        <div class="container">
            <ul class="projects" ref="projects">
                <app-work-item class="project-item" v-for="project in projects"
                :key="project.name" 
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
    <app-footer></app-footer>
</div>
</template>

<script>
import PageHeader from '@/components/page-header.vue';
import WorkItem from '@/components/work-item.vue';
import Footer from '@/components/footer.vue';

export default {
    components: {
        appPageHeader: PageHeader,
        appWorkItem: WorkItem,
        appFooter: Footer
    },
    mounted() {
        const items = [].slice.call(this.$refs["projects"].children);
        items.forEach((element, index) => {
            setTimeout(function() {
                element.classList.add('enter');
            }, index * 500)
        })
    },
    beforeDestroy() {
        const items = [].slice.call(this.$refs["projects"].children);
        items.forEach((element, index) => {
            setTimeout(function() {
                element.classList.remove('enter');
                element.classList.add('leave');
            }, index * 200)
        })
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
                    desc: 'Web application built in Vue.js that allows users to search for destinations or things to do, read reviews and add them to their bucket list. From their bucket list they can then keep track of when they visited a destination, and search hotels for that specific location.',
                    skills: ['HTML', 'SCSS', 'Vue', 'Vuex', 'Axios', 'TripAdvisor API', 'Hotels API'],
                    thumbnail: '/travel-list.jpg',
                    git: 'https://github.com/climber-sean/travel-list'
                },
                inkfinity: {
                    name: 'Inkfinity Tattoo',
                    desc: 'Basic website with Couch CMS integrated built in 2018 for a local tattoo shop. The CMS allows the client to update their opening times, change homepage text and upload images to the gallery for each artist.',
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

    .project-item {
        opacity: 0;
        &.enter {
            animation: shrink-fade-in 0.75s ease-out forwards;
        }
        &.leave {
            animation: right-fade-out 0.75s ease-out forwards;
        }
    }

    // &.enter {
    //     .project-item:nth-child(1) {
    //         animation: shrink-fade-in 1s ease-out forwards;
    //     }
    //     .project-item:nth-child(2) {
    //         animation: shrink-fade-in 1s 0.5s ease-out forwards;
    //     }
    //     .project-item:nth-child(3) {
    //         animation: shrink-fade-in 1s 1s ease-out forwards;
    //     }
    // }
}

.work-content {
    padding: 100px 0;
    background: $gradient-bg;

    @media handheld, only screen and (max-width: $tablet) {
        padding: 40px 0;
    }

    @media handheld, only screen and (max-width: $mobile) {
        padding: 20px 0;
    }
}
</style>