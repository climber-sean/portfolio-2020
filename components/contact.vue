<template>
    <div class="contact-container" ref="contact-container">
        <div class="contact-form" ref="contact-form">
            <div class="close-icon" @click="closeContact">
                <font-awesome-icon @click="closeContact" :icon="['fas', 'times']"></font-awesome-icon>
            </div>
            <div>
                <!-- <h3>Contact Me</h3> -->
                <form action="https://getsimpleform.com/messages?form_api_token=1ca7f3f2a9b1c486f33a635fa419f553" method="post">
                    <label for="Name">Name:</label>
                    <input v-model="name" type="text" placeholder="Name" name="Name">
                    <label for="Email">Email:</label>
                    <input v-model="email" type="email" placeholder="example@example.com" name="Email">
                    <label for="message">Message:</label>
                    <textarea v-model="message" name="message" id="" cols="30" rows="10" placeholder="Your message here...."></textarea>
                    <input :disabled="!checkForm" type="submit" value="Submit"> 
                </form>
            </div>
            <div class="contact-link">
                <a href="https://www.linkedin.com/in/sean-butlin-73307a16a/" target="_blank" title="LinkedIn" class="contact-link__item">
                    <font-awesome-icon aria-hidden="true" class="contact-link__item--icon" :icon="['fab', 'linkedin']"></font-awesome-icon> LinkedIn
                </a>
                <a href="mailto:seanbutlin@googlemail.com" title="Email me" class="contact-link__item">
                    <font-awesome-icon aria-hidden="true" class="contact-link__item--icon" :icon="['fas', 'envelope']"></font-awesome-icon> seanbutlin@googlemail.com
                </a>
                <a href="https://github.com/climber-sean" target="_blank" title="GitHub" class="contact-link__item">
                    <font-awesome-icon aria-hidden="true" class="contact-link__item--icon" :icon="['fab', 'github']"></font-awesome-icon> GitHub
                </a>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            name: null,
            email: null,
            message: null,
            submitButton: false
        }
    },
    methods: {
        closeContact() {
        this.$emit('close');
        }
    },
    computed: {
        checkForm() {
            if (this.name && this.email && this.message) {
               return true
            }
        }
    }
}
</script>

<style lang="scss">
@import '~assets/variables.scss';

    .contact-container {
        width: 100vw;
        height: 100vh;
        display: flex;
        justify-content: center;
        align-items: center;
        position: fixed;
        z-index: 10;
        top: 0;
        left: 0;
    }

    .contact-form {
        background: $primary-colour;
        padding: 20px;
        border-radius: 5px;
        display: flex;
        justify-content: center;
        align-items: center;
        position: relative;

        @media handheld, only screen and (max-width: $mobile) {
            flex-direction: column;
        }

        form {
            border-right: 1px solid white;
            padding-right: 15px;
            @media handheld, only screen and (max-width: $mobile) {
                border-right: none;
                border-bottom: 1px solid white;
                padding: 0 0 10px 0;
            }
        }
        @media handheld, only screen and (max-width: $mobile) {
            width: 280px;
        }
        .close-icon {
            position: absolute;
            top: -6px;
            right: -6px;
            width: 24px;
            height: 24px;
            padding: 5px;
            border-radius: 50%;
            background: whitesmoke;
            color: darken(red, 10%);
            display: flex;
            justify-content: center;
            align-items: center;
            box-shadow: 0 0 8px 4px rgba(0,0,0,0.4);
            cursor: pointer;
        }
        label, input, textarea {
            display: block;
            outline: none;
            width: 100%;
            padding: 5px 3px;
        }
        label {
            margin-bottom: 3px;
            color: white;
            font-family: Arial;
        }
        textarea {
            resize: none;
        }
        input[type="submit"] {
            &:disabled {
                opacity: 0.5;
                pointer-events: none;
            }
            box-shadow: none;
            margin: 10px 0 0 0;
            padding: 10px 18px;
            background-color: darken(green, 5%);
            border: none;
            color: white;
            border-radius: 3px;
            transition: all 0.2s linear;
            cursor: pointer;

            &:hover {
                background-color: $accent-colour;
            }
        }
    }

    .contact-link {
        padding-left: 15px;

        @media handheld, only screen and (max-width: $mobile) {
            padding-top: 10px;
        }

        &__item {
            display: flex;
            justify-content: flex-start;
            align-items: center;
            color: whitesmoke;
            font-size: 16px;
            margin: 5px 0;
            text-decoration: none;
            transition: all 0.2s linear;

            &:hover {
                color: $accent-colour;

                .contact-link__item--icon {
                    color: $accent-colour;
                }
            }

            &--icon {
                font-size: 28px;
                margin-right: 5px;
                color: whitesmoke;
                transition: all 0.2s linear;
            }
        }
    }
</style>
