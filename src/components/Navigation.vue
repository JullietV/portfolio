<template>
    <nav :class="$route.name">
        <div class="brand">
            <router-link to="/"><h1>JullietV</h1></router-link>
        </div>
        <div class="nav-links">
            <ul>
                <li><router-link to="/about">About Me</router-link></li>
                <li><router-link to="/portfolio">Portfolio</router-link></li>
                <li><router-link to="/contact">Contact Me</router-link></li>
            </ul>
        </div>
    </nav>
</template>

<script>
    export default {
        name: 'Navigation'
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
        }

        .nav-links {
            ul {
                display: flex;

                li {
                    font-size: 1.2rem;
                    margin-right: 10px;

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
    }
</style>