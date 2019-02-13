<template>
    <footer :class="$route.name">
        <div class="copy">
            <p>Hecho con <3, 2019.</p>
        </div>
        <ul>
            <li><a href="https://www.instagram.com/jullietv/" target="_blank">Instagram</a></li>
            <li><a href="https://codepen.io/JullietV/" target="_blank">Codepen</a></li>
            <li><a href="https://gitlab.com/JullietV" target="_blank">Gitlab</a></li>
            <li><a href="https://jullietv.wordpress.com/" target="_blank">Wordpress</a></li>
        </ul>
    </footer>
</template>

<script>
  export default {
    name: 'Footer',
    methods: {
      showRoute (route) {
        return this.$route.name === route
      }
    }
  }
</script>

<style lang="scss" scoped>
    @import '../assets/scss/variables';

    footer {
        font-size: .9rem;
        font-family: 'Nexa Bold', sans-serif;
        position: fixed;
        z-index: 9999;
        bottom: 0;
        margin-left: 5%;
        display: flex;
        align-items: center;
        justify-content: space-between;
        width: $max-width;

        ul {
            display: flex;
            vertical-align: middle;

            li {
                font-size: .9rem;
                margin-right: 10px;

                @media screen and (max-width: 500px) {
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


        &.home {
            .copy, ul a, ul li:after {
                color: $white;

                &:hover {
                    color: $blue !important;
                }
            }
        }

        &.about {
            .copy, ul a, ul li:after {
                color: $purple;

                &:hover {
                    color: darken($purple, 20%);
                }
            }
        }

        &.portfolio {
            .copy, ul a, ul li:after {
                color: $darker-green;

                &:hover {
                    color: darken($darker-green, 20%);
                }
            }
        }

        &.contact {
            .copy, ul a, ul li:after {
                color: $darker-blue;

                &:hover {
                    color: darken($darker-blue, 20%);
                }
            }
        }

        @media screen and (max-width: 768px) {
            flex-wrap: wrap;

            p {
                margin: 0;
            }

            .copy, ul {
                width: auto;
            }

        }
    }
</style>
