<template>
    <div class="portfolio">
        <grid :active="true"></grid>
    </div>
</template>

<script>
    import Grid from '@/components/Grid.vue'

    export default {
        name: 'Portfolio',
        components: {
            Grid
        }
    }
</script>

<style scoped>

</style>