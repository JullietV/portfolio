<template>
    <div class="about-wrapper">
        <div class="about-page">
            <div class="about-text">
                <h3>Soy una desarrolladora Front-End entusiasta por el diseño gráfico y diseño UX. Me especializo
                en el desarrollo de aplicaciones web en VueJS. Soy creativa, responsable y reisiliente. <b>¡Carpe Diem!</b></h3>
                <h2>Skills</h2>
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
                <h2>Experience</h2>
                <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Maiores praesentium quaerat quisquam vel
                    voluptatibus? Aut earum eveniet excepturi, officia provident quibusdam veritatis? Asperiores
                    consequuntur doloribus nihil tempora vel? Asperiores, voluptates!</p>
                <h2>Certifieds</h2>
                <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. A expedita incidunt ipsam itaque laborum
                    odit quia quibusdam soluta sunt tenetur. Blanditiis corporis deserunt distinctio dolor laborum omnis
                    quae voluptatibus voluptatum.</p>
            </div>
            <div class="about-img">
                <div class="img"></div>
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
        max-width: 90%;
        height: 100vh;
        margin: 0 5%;
        display: flex;
        flex-wrap: wrap;
        & > div {
            width: 50%;
            box-sizing: border-box;
            padding: 90px 15px 15px 0;
        }

        .about-text {
            text-align: left;

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
        }

        .about-img {
            padding-bottom: 0;
            text-align: center;

            .img {
                margin: 0 auto;
                height: 600px;
                width: 450px;
                background-image: url('../../public/img/me/carousel.jpg');
                background-size: auto 100%;
                animation: stepBy 20s steps(3) infinite alternate;
            }
        }
    }
</style>