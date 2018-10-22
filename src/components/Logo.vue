<template>
    <div class="logo-wrapper">
        <div :class="['logo', {'animated': isAnimatedHome}]"></div>
    </div>
</template>

<script>
    export default {
        name: 'Logo',
        props: {
            isAnimatedHome: {
                type: Boolean,
                default: false
            }
        }
    }
</script>

<style lang="scss" scoped>
    @import "../assets/scss/variables";

    @keyframes logo {
        100% {
            background-position: -597px;
        }
    }

    .logo-wrapper {
        width: 300px;
        height: 300px;
        background-color: $dark;
        border-radius: 50%;
        box-shadow: 0 0 59px 12px rgba(#000, .65);
        display: flex;
        align-items: center;
        justify-content: center;

        .logo {
            height: 228px;
            width: 150px;
            background-size: auto 100%;
            background-image: url('../assets/img/logo_changing_backwards.png');

            &.animated {
                animation: logo .5s steps(4);
                animation-delay: 5s;
                animation-fill-mode: backwards;
                animation-iteration-count: 2;
            }
        }
    }
</style>