<template>
    <div class="home-view">
        <grid :active="false"></grid>
        <logo class="home-logo" :isAnimatedHome="animationLogo"></logo>
    </div>
</template>

<script>
    // @ is an alias to /src
    import HelloWorld from '@/components/HelloWorld.vue'
    import Grid from '@/components/Grid.vue'
    import Logo from '@/components/Logo.vue'

    export default {
        name: 'home',
        components: {
            HelloWorld,
            Grid,
            Logo
        },
        data () {
            return {
                animationLogo: false
            }
        },
        created () {
            this.animationLogo = true
        }
    }
</script>

<style lang="scss">
    @import "../assets/scss/variables";

    .home-view {
        background-color: $dark;
        position: relative;

        .home-logo {
            position: absolute;
            top: calc(50vh - 150px);
            left: calc(50vw - 150px);
        }
    }
</style>