<template>
    <li class="work-item">
        <div class="work-item__image">
            <img :src="image" alt="Portfolio Project" class="res-img">
        </div>
        <div class="work-item__content">
            <h2>{{ name }}<span v-if="prog">In Progress</span></h2>
            <p>{{ desc }}</p>
            <ul class="work-item__content--skills">
                <span>Tools used:</span>
                <li v-for="skill in skills">
                    {{ skill }}
                </li>
            </ul>
            <div class="work-item__content--links">
                <div v-if="git" class="icon-container">
                    <a :href="git" target="_blank" :title="name">
                    <font-awesome-icon class="icon" :icon="['fab', 'github']"/>
                    GitHub
                    </a>
                </div>
                <div v-if="live" class="icon-container">
                    <a :href="live" target="_blank" :title="name">
                    <font-awesome-icon class="icon" :icon="['fas', 'window-maximize']"/>
                    Live
                    </a>
                </div>
            </div>
        </div>
    </li>
</template>

<script>
export default {
    props: {
        name: String,
        skills: Array,
        desc: String,
        image: String,
        git: String,
        live: String,
        prog: Boolean
    }
}
</script>

<style lang="scss">
@import '~assets/variables.scss';

.work-item {
    width: 70%;
    margin: 20px auto;
    display: flex;
    // background: linear-gradient(30deg, rgba(60,70,96,1) 0%, rgba(36,40,51,1) 50%);
    background: darken(whitesmoke, 20%);
    padding: 20px;
    border-radius: 5px;
    box-shadow: 0 0 8px 4px rgba(0,0,0,0.1);

    @media handheld, only screen and (max-width: $tablet) {
        width: 80%;
    }

    @media handheld, only screen and (max-width: $mobile) {
        flex-direction: column;
        padding: 10px;
        width: 90%;
    }

    &__image {
        width: 40%;
        padding: 10px;

        @media handheld, only screen and (max-width: $mobile) {
            width: 100%;
            padding: 0px;
        }
    }

    &__content {
        width: 60%;
        padding: 10px;
        color: lighten(black, 20%);
        @media handheld, only screen and (max-width: $mobile) {
            width: 100%;
            padding: 0px;
        }
        h2 {
            margin-top: 0;
            color: lighten(black, 10%);
            @media handheld, only screen and (max-width: $mobile) {
                text-align: center;
                margin-top: 5px;
                font-size: 22px;
            }
            span {
                display: block;
                color: darken(red, 10%);
                margin-top: -8px;
                font-size: 12px;
                text-transform: capitalize;
                letter-spacing: 1px;
                @media handheld, only screen and (max-width: $mobile) {
                    margin-top: -4px;
                }
            }
        }
        p {
            color: lighten(black, 20%);
        }
        span {
            display: block;
            margin: 5px 0;
            font-weight: 600;
            font-size: 20px;
            @media handheld, only screen and (max-width: $mobile) {
                font-size: 18px;
            }
        }
        &--skills {
            padding: 0;
            margin: 10px 0;
            list-style: none;

            li {
                margin: 0px 5px 0 0;
                display: inline-block;
                &:after {
                    content: ',';
                }
                &:last-child:after {
                    content: '';
                }
                @media handheld, only screen and (max-width: $mobile) {
                    font-size: 14px;
                }
            }
        }
        &--links {
            font-size: 20px;
            display: flex;
            margin-top: 10px;
            a {
                text-decoration: none;
                color: $accent-colour2;
                transition: all 0.2s linear;

                &:hover {
                    .icon {
                        color: whitesmoke
                    }

                    color: whitesmoke;
                }
            }
            .icon-container {
                margin-right: 10px;
            }
            .icon {
                color: $accent-colour2;
                font-size: 24px;
                transition: all 0.2s linear;
            }
        }
    }
}

</style>