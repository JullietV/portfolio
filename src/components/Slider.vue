<template>
    <div class="slider">
        <slick ref="slickFor"
               @beforeChange="handleBeforeChange"
               @afterChange="handleAfterChange"
               @reInit="reInit"
               class="slider-for"
               :options="slickForOptions">
            <a v-for="image in images" :href="image.src" target="_blank"><img :src="image.src" :alt="image.title"></a>
        </slick>
        <slick ref="slickNav"
               @beforeChange="handleBeforeChange"
               @afterChange="handleAfterChange"
               @reInit="reInit"
               class="slider-nav" :options="slickNavOptions">
            <a v-for="image in images" href="#"><div class="image-nav" :style="`background-image: url(${image.src})`"></div></a>
        </slick>
    </div>
</template>

<script>
    import Slick from 'vue-slick'
    import jquery from 'jquery'

    export default {
        name: 'Slider',
        components: {Slick},
        props: {
            images: {
                type: Array,
                default: function () {
                    return []
                }
            }
        },
        data () {
            return {
                slickForOptions: {
                    slidesToShow: 1,
                    slidesToScroll: 1,
                    arrows: false,
                    fade: true,
                    asNavFor: '.slider-nav'
                    // Any other options that can be got from plugin documentation
                },
                slickNavOptions: {
                    slidesToShow: 4,
                    slidesToScroll: 1,
                    asNavFor: '.slider-for',
                    dots: false,
                    centerMode: true,
                    focusOnSelect: true,
                    arrows: false
                }
            };
        },
        methods: {
            handleAfterChange (event, slick, currentSlide) {
                console.log('handleAfterChange', event, slick, currentSlide);
            },
            handleBeforeChange (event, slick, currentSlide, nextSlide) {
                console.log('handleBeforeChange', event, slick, currentSlide, nextSlide);
            },
            next () {
                this.$refs.slick.next();
            },

            prev () {
                this.$refs.slick.prev();
            },

            reInit () {
                // Helpful if you have to deal with v-for to update dynamic lists
                this.$nextTick(() => {
                    this.$refs.slickFor.reSlick();
                    this.$refs.slickNav.reSlick();
                });
            },
        },
        watch: {
            images: function (nv) {
                this.reInit()
                this.handleBeforeChange()
                this.handleAfterChange()
            }
        }
    }
</script>

<style lang="scss" scoped>
    @import "../assets/scss/variables";

    a {
        width: 100%;

        img {
            max-width: 100%;
        }
    }

    .slick-arrow, .slick-dots {
        display: none !important;
    }
</style>

<style lang="scss">
    @import "../assets/scss/variables";

    .slick-arrow, .slick-dots {
        display: none !important;
    }

    .slider-for {
        a {
            outline: none;
            display: flex !important;
            align-items: center;
            justify-content: center;
            width: 100%;
            height: calc(100vh - 310px);
            img {
                max-width: 93%;
                max-height: 100%;
                margin: auto;
                border-radius: 10px;
                box-shadow: 0 0 30px rgba($dark, .3);
            }
        }
    }

    .slider-nav {
        margin-top: 15px;
        .slick-current {
            a {
                opacity: 1;
            }
        }
        a {
            opacity: .6;
            outline: none;
            display: flex !important;
            align-items: center;
            justify-content: center;
            width: 100%;
            height: 100px !important;

            &:hover {
                opacity: 1;
            }

            > div {
                border-radius: 10px;
                width: 90%;
                height: 100%;
                background-size: cover;
            }
        }
    }
</style>