<template>
    <div :class="['grid', {'clickable': active}]">
        <div class="cover"></div>
        <div class="col">
            <div class="darker-image"></div>
            <div class="hover-effect">
                <i class="flaticon-magic-wand"></i>
            </div>
        </div>
        <div class="col">
            <div class="darker-image"></div>
            <div class="hover-effect">
                <i class="flaticon-magic-wand"></i>
            </div>
        </div>
        <div class="col">
            <div class="darker-image"></div>
            <div class="hover-effect">
                <i class="flaticon-magic-wand"></i>
            </div>
        </div>
        <div class="col">
            <div class="darker-image"></div>
            <div class="hover-effect">
                <i class="flaticon-magic-wand"></i>
            </div>
        </div>
        <div class="col">
            <div class="darker-image"></div>
            <div class="hover-effect">
                <i class="flaticon-magic-wand"></i>
            </div>
        </div>
        <div class="col">
            <div class="darker-image"></div>
            <div class="hover-effect">
                <i class="flaticon-magic-wand"></i>
            </div>
        </div>
        <div class="col">
            <div class="darker-image"></div>
            <div class="hover-effect">
                <i class="flaticon-magic-wand"></i>
            </div>
        </div>
        <div class="col">
            <div class="darker-image"></div>
            <div class="hover-effect">
                <i class="flaticon-magic-wand"></i>
            </div>
        </div>
        <div class="col">
            <div class="darker-image"></div>
            <div class="hover-effect">
                <i class="flaticon-magic-wand"></i>
            </div>
        </div>
        <div class="col">
            <div class="darker-image"></div>
            <div class="hover-effect">
                <i class="flaticon-magic-wand"></i>
            </div>
        </div>
        <div class="col">
            <div class="darker-image"></div>
            <div class="hover-effect">
                <i class="flaticon-magic-wand"></i>
            </div>
        </div>
        <div class="col">
            <div class="darker-image"></div>
            <div class="hover-effect">
                <i class="flaticon-magic-wand"></i>
            </div>
        </div>
        <div class="col">
            <div class="darker-image"></div>
            <div class="hover-effect">
                <i class="flaticon-magic-wand"></i>
            </div>
        </div>
        <div class="col">
            <div class="darker-image"></div>
            <div class="hover-effect">
                <i class="flaticon-magic-wand"></i>
            </div>
        </div>
        <div class="col">
            <div class="darker-image"></div>
            <div class="hover-effect">
                <i class="flaticon-magic-wand"></i>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        name: 'Grid',
        props: {
            projects: {
                type: Array,
                default: function () {
                    return []
                }
            },
            active: {
                type: Boolean,
                default: true
            }
        }
    }
</script>

<style lang="scss" scoped>
    @import "../assets/scss/variables";
    .grid {
        position: relative;
        display: grid;
        grid-template-columns: repeat(5, 1fr);
        grid-auto-rows: minmax(33.33vh, auto);

        .col {
            position: relative;
            background-image: url('https://picsum.photos/400/300/?random');

            .darker-image {
                position: absolute;
                top: 0;
                left: 0;
                right: 0;
                bottom: 0;
                @include background-opacity(#000, .5);
            }

            .hover-effect {
                display: none;
                /* position: absolute;
                top: 0; right: 0; bottom: 0; left: 0;
                $speed: 0.275s;
                transition: all $speed ease-in-out, visibility 0s $speed;
                visibility: hidden;
                will-change: transform;
                // Slides start below their columns, giving upward motion on hover
                transform: translateY(100%);*/
            }

            &:hover {
                .hover-effect {
                    position: absolute;
                    cursor: pointer;
                    @include background-opacity($blue, .8);
                    width: 100%;
                    height: 100%;
                    display: flex;
                    align-items: center;
                    justify-content: center;


                    i {
                        color: $white;
                        font-size: 2.5rem;
                    }
                }
            }
        }

        &.clickable {
            .cover {
                display: none;
            }
        }

        .cover {
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            z-index: 50;
        }
    }
</style>