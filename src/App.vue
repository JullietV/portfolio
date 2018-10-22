<template>
    <div id="app">
        <navigation></navigation>
        <router-view/>
    </div>
</template>

<script>
    import Navigation from './components/Navigation'

    export default {
        components: {
            Navigation
        }
    }
</script>

<style lang="scss">
    @import 'assets/fonts/icons/flaticon.css';

    @font-face {
        font-family: 'Nexa';
        src: url('assets/fonts/Nexa.otf');
        src: url('assets/fonts/Nexa.otf') format('embedded-opentype'),
        url('assets/fonts/Nexa.otf') format('woff2'),
        url('assets/fonts/Nexa.otf') format('woff'),
        url('assets/fonts/Nexa.otf') format('truetype'),
        url('assets/fonts/Nexa.otf') format('svg');
    }

    @font-face {
        font-family: 'Nexa Bold';
        src: url('assets/fonts/Nexa-bold.otf');
        src: url('assets/fonts/Nexa-bold.otf') format('embedded-opentype'),
        url('assets/fonts/Nexa-bold.otf') format('woff2'),
        url('assets/fonts/Nexa-bold.otf') format('woff'),
        url('assets/fonts/Nexa-bold.otf') format('truetype'),
        url('assets/fonts/Nexa-bold.otf') format('svg');
    }

    body {
        margin: 0;
        overflow: hidden;
    }

    #app {
        font-family: 'Nexa', sans-serif;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        text-align: center;
        color: #2c3e50;
    }

    a {
        text-decoration: none;
    }

    ul {
        list-style: none;
    }
</style>
