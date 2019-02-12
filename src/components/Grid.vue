<template>
    <div :class="['grid', {'clickable': active}]">
        <div class="cover"></div>
        <div v-for="(p, index) in shownProjects" @click="handleClick(p)"
             :style="`background-image: url(${p.thumbnail})`" class="col">
            <div class="darker-image"></div>
            <div class="hover-effect">
                <i class="flaticon-magic-wand"></i>
            </div>
        </div>
        <transition name="get-in">
            <div class="card-project" v-if="activeCard && active">
                <div class="card">
                    <div class="card-actions">
                        <div class="arrow left-arrow" @click="handlePrevProject(activeItem.index)">
                            <div class="flaticon-arrow-1"></div>
                        </div>
                        <div class="arrow right-arrow" @click="handleNextProject(activeItem.index)">
                            <div class="flaticon-arrow"></div>
                        </div>
                        <div class="close" @click="activeCard = false">
                            <i class="flaticon-close-button"></i>
                        </div>
                    </div>
                    <div class="counter"><span class="active">{{activeItem.index + 1}}</span> / <span class="total">{{this.projects.length}}</span>
                    </div>
                    <div class="card-content">
                        <div class="gallery">
                            <slider v-if="activeItem.item.slider.length > 0" :images="activeItem.item.slider"></slider>
                            <div v-if="!activeItem.item.slider.length > 0" class="">
                                No tengo imágenes de este proyecto :(
                            </div>
                        </div>
                        <div class="info">
                            <h2>{{activeItem.item.title}}</h2>
                            <p>{{activeItem.item.description}}</p>
                            <h3>Timeframe</h3>
                            <p>{{activeItem.item.timeframe}}</p>
                            <h3>Technologies</h3>
                            <ul class="techs">
                                <li v-for="tech in activeItem.item.tech">{{tech}}</li>
                            </ul>
                            <div class="visit-site" v-if="activeItem.item.link">
                                Visit Site<i class="flaticon-share"></i>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </transition>
    </div>
</template>

<script>
    import Slider from '@/components/Slider'

    export default {
        name: 'Grid',
        data () {
            return {
                shownProjects: [],
                interval: null,
                allProjects: [
                    {
                        id: 1,
                        title: 'Project To Team',
                        description: 'Aplicación Web para el manejo y la supervisión de grupos de trabajo, con múltiples' +
                            ' funcionalidades. Tales como: Organización y distribución de proyectos, manejo de usuarios, ' +
                            'manejo de grupos, creación y edición de actas, chat, entre otros. El desarrollo fue dividido ' +
                            'por etapas y ha ido escalando a medida que pasa el tiempo.',
                        timeframe: 'Un año, dividiendo el proyecto en diversas etapas.',
                        tech: ['HTML', 'CSS', 'JS', 'VUEJS', 'UX'],
                        link: 'http://projectoteam.com/',
                        slider: [
                            {
                                src: '/img/p2team/1.PNG',
                                title: 'rocket'
                            },
                            {
                                src: '/img/p2team/2.PNG',
                                title: 'rocket'
                            },
                            {
                                src: '/img/p2team/3.PNG',
                                title: 'rocket'
                            },
                            {
                                src: '/img/p2team/4.PNG',
                                title: 'rocket'
                            },
                            {
                                src: '/img/p2team/5.PNG',
                                title: 'rocket'
                            },
                            {
                                src: '/img/p2team/6.PNG',
                                title: 'rocket'
                            },
                        ],
                        thumbnail: '/img/p2team/thumb1.jpg'
                    },
                    {
                        id: 2,
                        title: 'AdsLab',
                        description: 'Aplicación Web para la automatización de Anuncios en diversos sitios de internet. Incluye estadísticas, ' +
                            'creación y manejo de anuncios.',
                        timeframe: 'Agosto 2018 - Actualidad',
                        tech: ['HTML', 'CSS', 'JS', 'VUEJS', 'UX'],
                        link: 'https://adslab.io/',
                        slider: [
                            {
                                src: `/img/adslab/1.png`,
                                title: 'rocket'
                            },
                            {
                                src: '/img/adslab/5.png',
                                title: 'rocket'
                            },
                            {
                                src: '/img/adslab/3.png',
                                title: 'rocket'
                            },
                            {
                                src: '/img/adslab/4.png',
                                title: 'rocket'
                            },
                            {
                                src: '/img/adslab/5.png',
                                title: 'rocket'
                            },
                            {
                                src: '/img/adslab/6.png',
                                title: 'rocket'
                            },
                            {
                                src: '/img/adslab/7.png',
                                title: 'rocket'
                            },
                            {
                                src: '/img/adslab/8.png',
                                title: 'rocket'
                            },
                            {
                                src: '/img/adslab/10.png',
                                title: 'rocket'
                            },
                        ],
                        thumbnail: `/img/adslab/thumb1.jpg`
                    },
                    {
                        id: 3,
                        title: 'CargoParts',
                        description: 'Tienda online de partes y accesorios automovilísticos',
                        timeframe: 'Enero 2017 - Abril 2017',
                        tech: ['HTML', 'CSS', 'JS', 'VUEJS', 'NUXT'],
                        link: null,
                        slider: [
                            {
                                src: '/img/cargo/CP-2.jpg',
                                title: 'rocket'
                            },
                            {
                                src: '/img/cargo/CP-4.jpg',
                                title: 'rocket'
                            },
                            {
                                src: '/img/cargo/CP-6.jpg',
                                title: 'rocket'
                            },
                            {
                                src: '/img/cargo/CP-7.jpg',
                                title: 'rocket'
                            },
                            {
                                src: '/img/cargo/CP-9.jpg',
                                title: 'rocket'
                            },
                            {
                                src: '/img/cargo/CP-12.jpg',
                                title: 'rocket'
                            },
                        ],
                        thumbnail: '/img/cargo/thumb1.jpg',
                    },
                    {
                        id: 4,
                        title: 'Amoblando',
                        description: 'Rediseño de una tienda online basada en AngularJS.',
                        timeframe: 'Abril 2017 - Marzo 2018 | El proyecto fue dividido en varias etapas en las que, ' +
                            'progresivamente se fueron añadiendo nuevas características',
                        tech: ['HTML', 'CSS', 'JS'],
                        link: 'https://www.amoblando.com.ar/#!/',
                        slider: [
                            {
                                src: '/img/amoblando/0.jpg',
                                title: 'rocket'
                            },
                            {
                                src: '/img/amoblando/1.png',
                                title: 'rocket'
                            },
                            {
                                src: '/img/amoblando/2.png',
                                title: 'rocket'
                            },
                            {
                                src: '/img/amoblando/3.png',
                                title: 'rocket'
                            },
                            {
                                src: '/img/amoblando/4.png',
                                title: 'rocket'
                            },
                            {
                                src: '/img/amoblando/5.png',
                                title: 'rocket'
                            },
                            {
                                src: '/img/amoblando/6.png',
                                title: 'rocket'
                            },
                        ],
                        thumbnail: '/img/amoblando/thumb1.jpg'
                    },
                    {
                        id: 5,
                        title: 'CDEM',
                        description: 'Aplicación web empleada para realizar tests de medicina en forma de práctica, ' +
                            'utilizando la gamificación como estrategia. Incluye estadísticas, contadores de juego,' +
                            ' medallas, badges, notas, etc. Todo lo que necesitas para estudiar de una manera más atractiva.',
                        timeframe: 'Agosto 2018 - Actualidad',
                        tech: ['HTML', 'CSS', 'JS', 'VUEJS', 'NUXT'],
                        link: null,
                        slider: [
                            {
                                src: '/img/cdem/01.jpg',
                                title: 'rocket'
                            },
                            {
                                src: '/img/cdem/2.jpg',
                                title: 'rocket'
                            },
                            {
                                src: '/img/cdem/3.jpg',
                                title: 'rocket'
                            },
                        ],
                        thumbnail: '/img/cdem/thumb1.jpg'
                    },
                    {
                        id: 6,
                        title: 'Firesoft',
                        description: 'Página web empresarial. Incluye Blog, buscador, portafolio, contactos y gestión de ' +
                            'presupuestos.',
                        timeframe: 'Enero 2018',
                        tech: ['HTML', 'CSS', 'JS', 'VUEJS', 'NUXT'],
                        link: 'https://www.firesoft.org/',
                        slider: [
                            {
                                src: '/img/firesoft/1.png',
                                title: 'rocket'
                            },
                            {
                                src: '/img/firesoft/2.png',
                                title: 'rocket'
                            },
                            {
                                src: '/img/firesoft/3.png',
                                title: 'rocket'
                            },
                            {
                                src: '/img/firesoft/4.png',
                                title: 'rocket'
                            },
                            {
                                src: '/img/firesoft/5.png',
                                title: 'rocket'
                            },
                            {
                                src: '/img/firesoft/6.png',
                                title: 'rocket'
                            },
                            {
                                src: '/img/firesoft/7.png',
                                title: 'rocket'
                            },
                            {
                                src: '/img/firesoft/8.png',
                                title: 'rocket'
                            },
                        ],
                        thumbnail: '/img/firesoft/thumb1.jpg'
                    },
                ],
                projects: [],
                activeItem: null,
                activeCard: false
            }
        },
        created () {
            this.projects = this.allProjects.slice(0)
            let self = this
            this.interval = setInterval(function () {
                self.randomizeGrid()
            }, 1500)
        },
        beforeDestroy () {
            clearInterval(this.interval)
        },
        components: {
            Slider
        },
        methods: {
            handleClick (item) {
                let i = this.projects.findIndex(e => e === item)
                this.activeItem = {
                    index: i,
                    item
                }
                this.activeCard = true
                console.log(this.activeItem)
            },
            handleNextProject (index) {
                if (index + 1 < this.projects.length) {
                    this.activeItem = {
                        index: index + 1,
                        item: this.projects[index + 1]
                    }
                } else {
                    this.activeItem = {
                        index: 0,
                        item: this.projects[0]
                    }
                }
            },
            handlePrevProject (index) {
                if (index > 0) {
                    this.activeItem = {
                        index: index - 1,
                        item: this.projects[index - 1]
                    }
                } else {
                    this.activeItem = {
                        index: this.projects.length,
                        item: this.projects[this.projects.length]
                    }
                }
            },
            randomizeGrid () {
                let p = this.allProjects
                let ctr = p.length
                let temp
                let index

                index = Math.floor(Math.random() * ctr)
                ctr--
                temp = p[ctr]
                p[ctr] = p[index]
                p[index] = temp

                this.shownProjects = p.slice(0, 15)
                /* console.log(p)
                console.log(this.shownProjects) */
            }
        },
        props: {
            active: {
                type: Boolean,
                default: true
            }
        },
    }
</script>

<style lang="scss" scoped>
    @import "../assets/scss/variables";

    .grid {
        position: relative;
        display: grid;
        grid-template-columns: repeat(3, 1fr);
        grid-auto-rows: minmax(50vh, auto);

        .col {
            cursor: pointer;
            position: relative;
            background-size: cover;
            overflow: hidden;
            background-position: center;
            // background-image: url('https://picsum.photos/400/300/?random');

            .darker-image {
                position: absolute;
                top: 0;
                left: 0;
                right: 0;
                bottom: 0;
                @include background-opacity(#000, .5);
            }

            .hover-effect {
                // display: none;
                /* position: absolute;
                top: 0; right: 0; bottom: 0; left: 0;
                $speed: 0.275s;
                transition: all $speed ease-in-out, visibility 0s $speed;
                visibility: hidden;
                will-change: transform;
                // Slides start below their columns, giving upward motion on hover
                transform: translateY(100%);*/
            }

            &:nth-child(even) {
                .hover-effect {
                    position: absolute;
                    top: auto;
                    left: -100%;
                }
                &:hover {
                    .hover-effect {
                        left: 0;
                        transition: all ease .25s;
                    }
                }
            }

            &:nth-child(odd) {
                .hover-effect {
                    position: absolute;
                    top: auto;
                    left: 100%;
                }
                &:hover {
                    .hover-effect {
                        left: 0;
                        transition: all ease .25s;
                    }
                }
            }

            &:hover {
                .hover-effect {
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

    .counter {
        left: calc(50% - 40px);
        bottom: -20px;
        position: absolute;
        width: 80px;
        height: 40px;
        background-color: $darker-blue;
        border-radius: 30px;
        display: flex;
        align-items: center;
        justify-content: center;
        font-family: "Nexa Light", sans-serif;
        color: rgba($purple, .8);

        .active {
            font-family: "Nexa Bold", sans-serif;
            font-size: 1.5rem;
            color: $purple;
        }
    }

    .card-project {
        position: absolute;
        top: 100px;
        width: 90%;
        left: 5%;
        height: calc(100vh - 150px);

        .card {
            display: flex;
            position: relative;
            background-color: $purple;
            border-radius: 8px;
            box-shadow: $shadow;
            width: 100%;
            height: 100%;

            .arrow {
                z-index: 999;
                position: absolute;
                display: flex;
                align-items: center;
                justify-content: center;
                width: 70px;
                height: 70px;
                background-color: $blue;
                top: calc(50% - 35px);
                border-radius: 50%;
                font-size: 2.7rem;
                color: $white;
                box-sizing: border-box;
                cursor: pointer;

                &:hover {
                    transition: all ease .5s;
                    background-color: $darker-blue;
                }

                &.left-arrow {
                    padding-right: 7px;
                    left: -35px;
                }
                &.right-arrow {
                    padding-left: 7px;
                    right: -35px;
                }
            }

            .close {
                z-index: 999;
                position: absolute;
                top: 15px;
                right: 15px;
                color: $white;
                font-size: 2.5rem;
                cursor: pointer;

                &:hover {
                    transition: .5s all ease;
                    transform: rotate(360deg);
                }
            }

            .card-content {
                width: 100%;
                display: flex;
                flex-wrap: wrap;
                > div {
                    width: 50%;
                }

                .counter {
                    width: 100%;
                }

                .gallery {
                    padding: 15px 50px;
                    // padding: 15px;
                    box-sizing: border-box;
                }

                .info {
                    // font-size: 120%;
                    padding: 0 15px 15px 15px;
                    box-sizing: border-box;
                    position: relative;
                    height: calc(100% - 20px);
                    text-align: left;
                    color: $white;
                    h2, h3 {
                        font-family: "Nexa Bold", sans-serif;
                        margin-bottom: 10px;
                    }

                    h2 {
                        font-size: 1.8rem;
                    }

                    .techs {
                        padding-left: 0;
                        display: flex;

                        li {
                            width: 50px;
                            height: 50px;
                            border-radius: 50%;
                            background-color: rgba($white, .8);
                            color: $purple;
                            font-family: "Nexa Bold", sans-serif;
                            display: flex;
                            align-items: center;
                            justify-content: center;
                            margin-right: 10px;
                            font-size: .8rem;
                        }
                    }

                    .visit-site {
                        position: absolute;
                        bottom: 15px;
                        right: 15px;
                        font-family: "Nexa Bold", sans-serif;
                        font-size: 3.5rem;

                        i {
                            margin-left: 15px;
                        }

                        &:hover {
                            color: $green;
                            cursor: pointer;
                            transition: .5s ease all;
                        }
                    }
                }
            }
        }
    }

    @keyframes get-in {
        0% {
            height: calc(100vh - 150px);
            overflow: hidden;
            top: 100%;
        }
        70% {
            position: absolute;
            top: 80px;
        }
        100% {
            top: 100px;
        }
    }

    .get-in-enter-active, .get-in-leave-active {
        animation: get-in .5s;
    }

    .get-in-enter, .get-in-leave-to {
        animation: get-in .5s reverse;
    }
</style>