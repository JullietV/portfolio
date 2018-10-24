<template>
    <div class="about-wrapper">
        <div class="about-page">
            <div class="about-text">
                <h3>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Cum dolor dolore, doloremque dolores
                    doloribus expedita explicabo, incidunt ipsum maxime molestias, mollitia odio perferendis quam
                    quisquam repellendus sapiente sed vel velit!</h3>
                <h2>Skills</h2>
                <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Dolor, dolorem ducimus eius illo ipsum
                    magnam molestias perspiciatis porro vel veniam. Accusantium, adipisci aspernatur dolore eligendi
                    exercitationem iste nisi officia. Inventore?</p>
                <h2>Experience</h2>
                <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Maiores praesentium quaerat quisquam vel
                    voluptatibus? Aut earum eveniet excepturi, officia provident quibusdam veritatis? Asperiores
                    consequuntur doloribus nihil tempora vel? Asperiores, voluptates!</p>
                <h2>Certifieds</h2>
                <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. A expedita incidunt ipsam itaque laborum
                    odit quia quibusdam soluta sunt tenetur. Blanditiis corporis deserunt distinctio dolor laborum omnis
                    quae voluptatibus voluptatum.</p>
            </div>
            <div class="about-img"></div>
        </div>
    </div>
</template>
<style lang="scss" scoped>
    @import '../assets/scss/variables';

    .about-wrapper {
        background-image: url('../assets/img/city.png');
        background-position: bottom center;
    }

    .about-page {
        max-width: 90%;
        height: 100vh;
        margin: 0 5%;
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
        }
    }
</style>