<template>
    <div class="about-wrapper">
        <div class="about-page">
            <div class="about-img">
            </div>
            <div class="about-text">
                <h3>Soy una desarrolladora Front-End entusiasta por el diseño gráfico y diseño UX. Me especializo
                en el desarrollo de aplicaciones web en VueJS. Soy creativa, responsable y reisiliente. <b>¡Carpe Diem!</b></h3>
                <h2>Habilidades</h2>
                <ul class="skills-list">
                    <li>
                        <div class="skill-name">
                            HTML, CSS y JS
                        </div>
                        <div class="skill-bar">
                            <div class="bar b95"></div>
                        </div>
                    </li>
                    <li>
                        <div class="skill-name">
                            VueJS, NUXT
                        </div>
                        <div class="skill-bar">
                            <div class="bar b80"></div>
                        </div>
                    </li>
                    <li>
                        <div class="skill-name">
                            Supervisión
                        </div>
                        <div class="skill-bar">
                            <div class="bar b60"></div>
                        </div>
                    </li>
                    <li>
                        <div class="skill-name">
                            Diseño Web
                        </div>
                        <div class="skill-bar">
                            <div class="bar b70"></div>
                        </div>
                    </li>
                    <li>
                        <div class="skill-name">
                            Inglés
                        </div>
                        <div class="skill-bar">
                            <div class="bar b80"></div>
                        </div>
                    </li>
                    <li>
                        <div class="skill-name">
                            Contacto con Clientes
                        </div>
                        <div class="skill-bar">
                            <div class="bar b80"></div>
                        </div>
                    </li>
                </ul>
                <h2>Experiencia</h2>
                <ul class="experience-list">
                    <li>
                        <div class="experience-head">
                            <div class="date"><span>2014</span><strong>Act.</strong></div>
                            <div class="name">
                                <h3>Freelancer</h3>
                            </div>
                        </div>
                    </li>
                    <li>
                        <div class="experience-head">
                            <div class="date"><span>2014</span><strong>Act.</strong></div>
                            <div class="name">
                                <h3>Desarrolladora Front</h3>
                                <h4>Firesoft International</h4>
                            </div>
                        </div>
                        <ul class="experience-content">
                            <li>
                                Supervisión de diversos equipos de trabajo.
                            </li>
                            <li>Supervisión del departamento de Diseño.</li>
                            <li>Desarrollo web responsivo.</li>
                            <li>Desarrollo de Aplicaciones Web con VueJS y NUXT.</li>
                            <li>Conexión con APIs.</li>
                        </ul>
                    </li>
                </ul>
                <h2>Certificados</h2>
                <ul class="certifieds">
                    <li>
                        <div class="date">2016</div>
                        <div class="text">
                            <h3>Curso de Programación Básica</h3>
                            <h4>Platzi</h4>
                        </div>
                    </li>
                    <li>
                        <div class="date">2016</div>
                        <div class="text">
                            <h3>Curso de Marca Personal</h3>
                            <h4>Platzi</h4>
                        </div>
                    </li>
                    <li>
                        <div class="date">2016</div>
                        <div class="text">
                            <h3>Curso de desarrollo Web Online</h3>
                            <h4>Platzi</h4>
                        </div>
                    </li>
                    <li>
                        <div class="date">2016</div>
                        <div class="text">
                            <h3>Curso de Responsive Design</h3>
                            <h4>Platzi</h4>
                        </div>
                    </li>
                    <li>
                        <div class="date">2016</div>
                        <div class="text">
                            <h3>Curso de PostCSS</h3>
                            <h4>Platzi</h4>
                        </div>
                    </li>
                </ul>
            </div>

        </div>
    </div>
</template>
<script>
    export default {
        name: 'about',
        data () {
            return {

            }
        },
        methods: {
        }
    }
</script>
<style lang="scss" scoped>
    @import '../assets/scss/variables';

    @keyframes stepBy {
        from { background-position: 0 }
        to   { background-position: 100% }
    }

    .about-wrapper {
        // background-image: url('../assets/img/city.png');
        background-position: bottom center;
    }

    .about-page {
        display: flex;
        flex-wrap: wrap;
        height: 100vh;

        & > div {
            max-height: 100%;
            width: 50%;
            box-sizing: border-box;
            padding: 90px 15px 15px 0;
            overflow: auto;
        }

        .about-text {
            padding-right: 5%;
            max-height: 100%;
            text-align: left;
            padding-bottom: 3rem;


            h2 {
                font-family: 'Nexa Bold', sans-serif;
                color: $purple;
            }

            ul {
                padding:0;
                margin: 0;

                &.skills-list {
                    li {
                        margin-bottom: 10px;
                        display: flex;
                        flex-wrap: wrap;
                        justify-content: space-between;

                        .skill-name {

                        }

                        .skill-bar {
                            width: 50%;
                            background-color: rgba(0,0,0,.05);
                            border-radius: 60px;
                            overflow: hidden;

                            .bar {
                                background-color: $purple;
                                height: 100%;
                                border-radius: 60px;
                                background: $darker-purple;
                                background: -moz-linear-gradient(left, $darker-purple 0%, $purple 100%);
                                background: -webkit-gradient(left top, right top, color-stop(0%, $darker-purple), color-stop(100%, $purple));
                                background: -webkit-linear-gradient(left, $darker-purple 0%, $purple 100%);
                                background: -o-linear-gradient(left, $darker-purple 0%, $purple 100%);
                                background: -ms-linear-gradient(left, $darker-purple 0%, $purple 100%);
                                background: linear-gradient(to right, $darker-purple 0%, $purple 100%);
                                filter: progid:DXImageTransform.Microsoft.gradient( startColorstr='#343757', endColorstr='#5b5f97', GradientType=1 );

                                &.b95 {
                                    width: 95%;
                                }
                                &.b70 {
                                    width: 70%;
                                }
                                &.b80 {
                                    width: 80%;
                                }
                                &.b60 {
                                    width: 60%;
                                }
                            }
                        }
                    }
                }

            }

            .experience-list {
                > li {
                    margin-bottom: 1rem;
                }

                .experience-head {
                    display: flex;
                    align-items: center;

                    h3, h4 {
                        margin: 0;
                    }

                    h3 {
                        font-family: 'Nexa Bold', sans-serif;
                    }

                    h4 {
                        color: $purple;

                    }
                }

                .experience-content {
                    padding-left: 60px;

                    li {
                        &:before {
                            content: '- ';
                        }
                    }
                }

                .date {
                    background-color: $purple;
                    color: $green;
                    width: 50px;
                    height: 50px;
                    border-radius: 50%;
                    position: relative;
                    margin-right: 15px;
                    font-family: 'Nexa Bold', sans-serif;


                    span {
                        display: block;
                        top: 15px;
                        left: 6px;
                        position: absolute;
                        font-size: .8rem;
                        opacity: .8;
                    }

                    strong {
                        font-size: 1.3rem;
                        display: block;
                        position: absolute;
                        bottom: 0;
                        right: 0;
                        text-shadow: 1px 1px 1px rgba(#000, .8);
                    }
                }
            }

            .certifieds {

                li {
                    display: flex;
                    align-items: center;
                    margin-bottom: 1rem;

                    h3, h4 {
                        margin: 0;
                    }
                }
                .date {
                    width: 40px;
                    height: 40px;
                    background-color: $purple;
                    color: $green;
                    border-radius: 50%;
                    display: flex;
                    align-items: center;
                    justify-content: center;
                    margin-right: 15px;
                    font-size: .8rem;
                    font-family: 'Nexa Bold', sans-serif;
                }
            }
        }

        .about-img {
            padding-left: 6%;
            max-height: 98vh;
            padding-bottom: 0;
            text-align: center;
            display: flex;
            align-items: flex-end;
            background-image: url('../../public/img/me/yo-landa.png');
            background-size: contain;
            background-position: center;
            background-repeat: no-repeat;

            .img {
                position: fixed;
                left: calc(50% + 225px);
                margin: 0 auto;
                height: 600px;
                width: 450px;
                background-image: url('../../public/img/me/carousel.jpg');
                background-size: auto 100%;
                animation: stepBy 20s steps(3) infinite alternate;
            }
        }

        @media screen and (max-width: 768px) {
            padding-top: 7rem;
            display: block;
            height: 100vh;
            & > div {
                padding: 0;
                width: 90%;
                margin: 0 auto;
            }

            .about-text {
                max-height: none;

                h2, ul {
                    display: none;
                }

                h3 {
                    text-align: center;
                }
            }

            .about-img {

                height: 400px;
            }
        }
    }
</style>
