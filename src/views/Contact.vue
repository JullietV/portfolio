<template>
    <div class="contact-wrapper">
        <form @submit.prevent="handleSubmit" id="theForm" class="contact-form-wrapper">
            <div class="input-group">
                <input type="text" id="subject" name="subject" required v-model="subject">
                <span class="highlight"></span>
                <span class="bar"></span>
                <label for="subject">Asunto</label>
            </div>
            <div class="input-group">
                <input type="text" id="name" name="from_name" required v-model="name">
                <span class="highlight"></span>
                <span class="bar"></span>
                <label for="name">Nombre</label>
            </div>
            <div class="input-group">
                <input type="email" id="email" name="from_email" required v-model="email">
                <span class="highlight"></span>
                <span class="bar"></span>
                <label for="email">Email</label>
            </div>
            <div class="input-group">
                <textarea id="message" name="message_html" required v-model="message"></textarea>
                <span class="highlight"></span>
                <span class="bar"></span>
                <label for="message">Mensaje</label>
            </div>
            <div class="loader" v-if="loading">
                <div class="hollow-dots-spinner">
                    <div class="dot"></div>
                    <div class="dot"></div>
                    <div class="dot"></div>
                </div>
            </div>
            <div class="answer" v-if="answer">
                {{answer}}
            </div>
            <button type="submit"><i class="flaticon-paper-plane-2"></i></button>
        </form>
    </div>
</template>

<script>
    let emailjs = require('emailjs-com')
    export default {
        name: 'Contact',
        data () {
            return {
                subject: null,
                email: null,
                name: null,
                message: null,
                loading: false,
                answer: null
            }
        },
        computed: {
            checkFields () {
                if (this.subject) {
                    if (this.email) {
                        if (this.name) {
                            if (this.message) {
                                return true
                            }
                        }
                    }
                }

                return false
            }
        },
        methods: {
            handleSubmit () {
                let self = this
                if (this.checkFields) {
                    this.loading = true
                    emailjs.sendForm('gmail', 'template_HCzaKkuo', '#theForm', 'user_3FERlUek61v4BGACejrEl')
                        .then((response) => {
                            self.loading = false
                            self.subject = null
                            self.email = null
                            self.name = null
                            self.message = null
                            self.answer = 'El mensaje se ha enviado satisfactoriamente!'
                        }, (err) => {
                            this.loading = false
                            self.answer = 'Vaya, no hemos podido enviar el mensaje, inténtalo de nuevo.'
                        });
                }
            }
        }
    }
</script>

<style lang="scss" scoped>
    @import '../assets/scss/variables';

    .contact-wrapper {
        display: flex;
        align-items: center;
        justify-content: center;
        height: 100vh;
        background-image: url(../assets/img/airplanes.png);
    }

    .contact-form-wrapper {
        background-color: rgba($blue, .7);
        padding: 30px;
        width: 500px;
        max-width: 90%;
        flex-wrap: wrap;
        display: flex;
        align-items: center;
        justify-content: center;
        position: relative;
        border-radius: 10px;
        box-shadow: 0 0 30px rgba($dark, .1);
    }

    .input-group {
        position: relative;
        margin-bottom: 45px;
    }

    input, textarea {
        font-size: 18px;
        padding: 10px 10px 10px 5px;
        display: block;
        width: 300px;
        border: none;
        background-color: transparent;
        border-bottom: 2px solid rgba($purple, .6);
        resize: none;
        color: $purple;
        font-family: 'Nexa Light', sans-serif;
    }

    input:focus, textarea:focus {
        outline: none;
    }

    /* LABEL ======================================= */
    label {
        color: rgba($purple, .6);
        font-size: 18px;
        font-weight: 600;
        position: absolute;
        pointer-events: none;
        left: 5px;
        top: 10px;
        transition: 0.2s ease all;
        -moz-transition: 0.2s ease all;
        -webkit-transition: 0.2s ease all;
    }

    /* active state */
    input:focus ~ label, input:valid ~ label,
    textarea:focus ~ label, textarea:valid ~ label {
        top: -20px;
        font-size: 14px;
        color: #5264AE;
    }

    /* BOTTOM BARS ================================= */
    .bar {
        position: relative;
        display: block;
        width: 100%;
    }

    .bar:before, .bar:after {
        content: '';
        height: 2px;
        width: 0;
        bottom: 1px;
        position: absolute;
        background: #5264AE;
        transition: 0.2s ease all;
        -moz-transition: 0.2s ease all;
        -webkit-transition: 0.2s ease all;
    }

    .bar:before {
        left: 50%;
    }

    .bar:after {
        right: 50%;
    }

    /* active state */
    input:focus ~ .bar:before, input:focus ~ .bar:after,
    textarea:focus ~ .bar:before, textarea:focus ~ .bar:after {
        width: 50%;
    }

    /* HIGHLIGHTER ================================== */
    .highlight {
        position: absolute;
        height: 60%;
        width: 100px;
        top: 25%;
        left: 0;
        pointer-events: none;
        opacity: 0.5;
    }

    /* active state */
    input:focus ~ .highlight,
    textarea:focus ~ .highlight {
        -webkit-animation: inputHighlighter 0.3s ease;
        -moz-animation: inputHighlighter 0.3s ease;
        animation: inputHighlighter 0.3s ease;
    }

    /* ANIMATIONS ================ */
    @-webkit-keyframes inputHighlighter {
        from {
            background: #5264AE;
        }
        to {
            width: 0;
            background: transparent;
        }
    }

    @-moz-keyframes inputHighlighter {
        from {
            background: #5264AE;
        }
        to {
            width: 0;
            background: transparent;
        }
    }

    @keyframes inputHighlighter {
        from {
            background: #5264AE;
        }
        to {
            width: 0;
            background: transparent;
        }
    }

    button {
        position: absolute;
        width: 70px;
        height: 70px;
        background-color: $purple;
        outline: none;
        border: 0;
        border-radius: 50%;
        color: $white;
        font-size: 50px;
        bottom: -35px;
        right: -35px;
        transition: .25s ease all;

        &:hover {
            cursor: pointer;
            transform: scale(1.1);
            transition: .25s ease all;
        }
    }

    .loader {
        display: flex;
        justify-content: center;
        width: 100%;
    }

    .hollow-dots-spinner, .hollow-dots-spinner * {
        box-sizing: border-box;
    }

    .hollow-dots-spinner {
        height: 15px;
        width: calc(30px * 3);
    }

    .hollow-dots-spinner .dot {
        width: 15px;
        height: 15px;
        margin: 0 calc(15px / 2);
        border: calc(15px / 5) solid $purple;
        border-radius: 50%;
        float: left;
        transform: scale(0);
        animation: hollow-dots-spinner-animation 1000ms ease infinite 0ms;
    }

    .hollow-dots-spinner .dot:nth-child(1) {
        animation-delay: calc(300ms * 1);
    }

    .hollow-dots-spinner .dot:nth-child(2) {
        animation-delay: calc(300ms * 2);
    }

    .hollow-dots-spinner .dot:nth-child(3) {
        animation-delay: calc(300ms * 3);

    }

    @keyframes hollow-dots-spinner-animation {
        50% {
            transform: scale(1);
            opacity: 1;
        }
        100% {
            opacity: 0;
        }
    }
</style>