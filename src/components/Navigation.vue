<template>
    <nav :class="$route.name">
        <div class="brand">
            <router-link to="/"><h1>JullietV</h1></router-link>
        </div>
        <div class="nav-links">
            <ul>
                <li v-if="!showRoute('about')">
                    <router-link to="/about">Acerca de Mi</router-link>
                </li>
                <li v-if="!showRoute('portfolio')">
                    <router-link to="/portfolio">Portafolio</router-link>
                </li>
                <li v-if="!showRoute('contact')">
                    <router-link to="/contact">¡Contactame!</router-link>
                </li>
            </ul>
        </div>
    </nav>
</template>

<script>
    export default {
        name: 'Navigation',
        methods: {
            showRoute (route) {
                return this.$route.name === route
            }
        }
    }
</script>

<style lang="scss" scoped>
    @import '../assets/scss/variables';

    nav {
        position: fixed;
        z-index: 9999;
        margin-left: 5%;
        display: flex;
        align-items: center;
        justify-content: space-between;
        width: $max-width;

        .brand {
            font-family: 'Nexa Bold';
            font-size: 2.5rem;

            h1 {
                margin: 10px 0;
            }

            @media screen and (max-width: 500px) {
                font-size: 1.25rem;
            }

            @media screen and (max-width: 800px) {
                font-size: 2rem;
            }
        }

        .nav-links {
            ul {
                display: flex;
                vertical-align: middle;

                li {
                    font-size: 1.2rem;
                    margin-right: 10px;

                    @media screen and (max-width:500px) {
                        font-size: 1rem;
                    }

                    &:after {
                        content: '•';
                        margin-left: 10px;
                    }

                    &:last-child {
                        &:after {
                            content: '';
                            margin-left: 0;
                        }
                    }
                }
            }
        }

        &.home {
            .brand h1, .nav-links a, .nav-links li:after {
                color: $white;

                &:hover {
                    color: $blue !important;
                }
            }
        }

        &.about {
            .brand h1, .nav-links a, .nav-links li:after {
                color: $purple;

                &:hover {
                    color: darken($purple, 20%);
                }
            }
        }

        &.portfolio {
            .brand h1, .nav-links a, .nav-links li:after {
                color: $darker-green;

                &:hover {
                    color: darken($darker-green, 20%);
                }
            }
        }

        &.contact {
            .brand h1, .nav-links a, .nav-links li:after {
                color: $darker-blue;

                &:hover {
                    color: darken($darker-blue, 20%);
                }
            }
        }

        @media screen and (max-width: 768px) {
            flex-wrap: wrap;

            .brand h1 {
                margin-bottom: 0;
            }

            .brand, .nav-links {
                width: 100%;
            }
        }
    }
</style>
