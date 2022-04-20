<template>
<div class="hello">

    <img class="logo" :src="pantalla.logo.url" alt="">
    <br>
    <br>
    <h1 class="tit-por">{{ pantalla.name_screen }}</h1>

    <div class="container animate__animated animate__bounce con-port">

        <div class="row">

            <div class="wrapper">

                <button class="slide_from_left" data-toggle="modal" data-target="#modal1">GALERIA INTERIOR</button>

                <button class="slide_from_right" data-toggle="modal" data-target="#modal2">ESPACIOS COMUNES</button>
                <button class="grow_skew_forward" data-toggle="modal" data-target="#modal3">BROCHURE</button>
                <button class="grow_spin" data-toggle="modal" data-target="#modal4">PLANTAS</button>
                <button class="grow_skew_forward" data-toggle="modal" data-target="#modal5">UBICACION &rarr;</button>
                <button class="grow_skew_backward" data-toggle="modal" data-target="#modal6">CARACTERISTICAS &larr;</button>
                <button class="grow_spin">VIDEOS</button>
            </div>
            <a data-toggle="modal" data-target="#modal1">
                <div class="col col-4">
                    <div style="display: none;" class="tit-catego">GALERIA INTERIOR</div>
                    <div class="corner"></div>
                    <img style="display: none;" class="img-pan" src="img/iconos/camara.png" alt="">
                </div>
            </a>
            <div class="modal fade" id="modal1" tabindex="-1" role="dialog" aria-labelledby="exampleModalLabel" aria-hidden="true">
                <div class="modal-dialog" role="document">
                    <div class="modal-content">
                        <div class="modal-header">
                            <h2 class="tit-por">GALERIA INTERIOR</h2>
                            <button type="button" class="close" data-dismiss="modal" aria-label="Close">
                                <span aria-hidden="true">&times;</span>
                            </button>
                        </div>
                        <div class="modal-body">
                            <br>
                            <br>
                            <br>
                            <br>
                            <br>
                            <br>
                            <carousel>
                                <div v-for="gallery1 in gallery_1" :key="gallery1.id">
                                    <img :src="gallery1.media[0].url" height="300px" />
                                </div>
                            </carousel>
                        </div>
                        <div class="modal-footer">

                        </div>
                    </div>
                </div>
            </div>

            <a data-toggle="modal" data-target="#modal2">
                <div class="col-lg-4">
                    <div style="display: none;" class="tit-catego">ESPACIOS COMUNES</div>
                    <div class="corner"></div>
                    <img style="display: none;" class="img-pan" src="img/iconos/sala.png" alt="">
                </div>
            </a>
            <div class="modal fade" id="modal2" tabindex="-1" role="dialog" aria-labelledby="exampleModalLabel" aria-hidden="true">

                <div class="modal-dialog" role="document">
                    <div class="modal-content">
                        <div class="modal-header">
                            <h2 class="tit-por">ESPACIOS COMUNES</h2>
                            <button type="button" class="close" data-dismiss="modal" aria-label="Close">
                                <span aria-hidden="true">&times;</span>
                            </button>
                        </div>
                        <div class="modal-body">
                            <br>
                            <br>
                            <br>
                            <br>
                            <br>
                            <br>
                            <carousel>
                                <div v-for="gallery2 in gallery_2" :key="gallery2.id">
                                    <img :src="gallery2.media[0].url" height="300px" />
                                </div>
                            </carousel>
                        </div>
                        <div class="modal-footer">

                        </div>
                    </div>
                </div>
            </div>
        </div>
        <a data-toggle="modal" data-target="#modal3">
            <div class="col-lg-4">
                <div style="display: none;" class="tit-catego">BROCHURE</div>
                <div class="corner"></div>
                <img style="display: none;" class="img-pan" src="img/iconos/brochure1.png" alt="">
            </div>
        </a>

        <div class="modal fade" id="modal3" tabindex="-1" role="dialog" aria-labelledby="exampleModalLabel" aria-hidden="true">
            <div class="modal-dialog" role="document">
                <div class="modal-content">
                    <div class="modal-header">
                        <h5 class="modal-title" id="exampleModalLabel">Modal title</h5>
                        <button type="button" class="close" data-dismiss="modal" aria-label="Close">
                            <span aria-hidden="true">&times;</span>
                        </button>
                    </div>

                    <iframe :src="pantalla.brochure" width="100%" height="1000" seamless="seamless" scrolling="no" frameBorder="0" allowFullScreen></iframe>

                </div>
            </div>
        </div>
    </div>

    <a data-toggle="modal" data-target="#modal4">
        <div class="col-lg-4">
            <div style="display: none;" class="tit-catego">PLANTAS</div>
            <div class="corner"></div>
            <img style="display: none;" class="img-pan" src="img/iconos/plantas1.png" alt="">
        </div>
    </a>
    <div class="modal fade" id="modal4" tabindex="-1" role="dialog" aria-labelledby="exampleModalLabel" aria-hidden="true">
        <div class="modal-dialog" role="document">
            <div class="modal-content">
                <div class="modal-header">
                    <h2 class="tit-por">PLANTAS</h2>
                    <button type="button" class="close" data-dismiss="modal" aria-label="Close">
                        <span aria-hidden="true">&times;</span>
                    </button>
                </div>
                <br>
                <br>
                <br>

                <planok :id="pantalla.plants" height="300px"></planok>

            </div>
        </div>
    </div>
    <a data-toggle="modal" data-target="#modal5">
        <div class="col-lg-4">
            <div style="display: none;" class="tit-catego">UBICACIÓN</div>
            <div class="corner"></div>
            <img style="display: none;" class="img-pan" src="img/iconos/ubicacion5.png" alt="">
        </div>
    </a>
    <div class="modal fade" id="modal5" tabindex="-1" role="dialog" aria-labelledby="exampleModalLabel" aria-hidden="true">
        <div class="modal-dialog" role="document">
            <div class="modal-content">
                <div class="modal-header">
                    <h2 class="tit-por">UBICACIÓN Y ENTORNO</h2>
                    <button type="button" class="close" data-dismiss="modal" aria-label="Close">
                        <span aria-hidden="true">&times;</span>
                    </button>
                </div>
                <div class="modal-body">
                    <div class="container">
                        <div class="row">
                            <div class="col-6">
                                <img class="img-mapa" :src="pantalla.caracteristica_1.url">
                            </div>
                            <div class="col-6">
                                <iframe src="https://www.google.com/maps/embed?pb=!1m14!1m8!1m3!1d6660.474689230514!2d-70.507505!3d-33.417056!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x9662cc36a134db21%3A0x6c72e6ba51161f9!2sFrancisco%20Bulnes%20Correa%203640%2C%20Las%20Condes%2C%20Regi%C3%B3n%20Metropolitana!5e0!3m2!1ses-419!2scl!4v1640119497386!5m2!1ses-419!2scl" width="540" height="324" style=" border: #2c3e50 8px solid; border-radius: 15px;" allowfullscreen="" loading="lazy"></iframe>
                            </div>
                           
                    </div>
                    <carousel :responsive="{0:{items:1,nav:false},800:{items:3,nav:false}}">
                        <div v-for="gallery2 in gallery_2" :key="gallery2.id">
                            <img :src="gallery2.media[0].url" height="" />
                        </div>
                    </carousel>
                </div>

            </div>
        </div>
    </div>
    </div>

    <a data-toggle="modal" data-target="#modal6">
        <div class="col-lg-4">
            <div style="display: none;" class="tit-catego">CARACTERISTICAS</div>
            <div class="corner"></div>
            <img style="display: none;" class="img-pan" src="img/iconos/libro.png" alt="">
        </div>
    </a>
    <div class="modal fade" id="modal6" tabindex="-1" role="dialog" aria-labelledby="exampleModalLabel" aria-hidden="true">
        <div class="modal-dialog" role="document">
            <div class="modal-content">
                <div class="modal-header">
                    <h2 class="tit-por">CARACTERISTICAS</h2>
                    <button type="button" class="close" data-dismiss="modal" aria-label="Close">
                        <span aria-hidden="true">&times;</span>
                    </button>
                </div>
                <div class="modal-body">

                    <img class="img-caract" :src="pantalla.caracteristica_2.url">

                </div>

            </div>
        </div>
    </div>
</div>

</template>

<script>
import axios from 'axios';
import carousel from "vue-owl-carousel";
import planok from "../components/planok/PlanOk.vue";
export default {
    components: {
        planok,
        carousel,

    },

    data() {

        return {
            pantalla: null,
            gallery_1: [],
            gallery_2: [],

        }
    },
    methods: {
        obtenerPantallas() {
            var config = {
                method: "get",
                url: `http://127.0.0.1:8000/api/v1/pantallas/${this.$route.params.id}`,
                headers: {
                    Authorization: "Bearer 1|Y0qntxaGzCK9Ya9GkLbp36CvWsRLFfOLjxnvMrRW",
                },
            };

            axios(config)
                .then((response) => {
                    //traemos todos los datos de todos de la pantalla
                    console.log(JSON.parse(JSON.stringify(response.data)));
                    // traemos todos los datos de pantalla especifico segun URL

                    this.pantalla = JSON.parse(JSON.stringify(response.data.data));

                    // traemos la galeria interior

                    this.gallery_1 = JSON.parse(
                        JSON.stringify(response.data.data.id_gallery_1s)
                    );
                    // traemos la galeria espacios comunes
                    this.gallery_2 = JSON.parse(
                        JSON.stringify(response.data.data.id_gallery_2s)
                    );

                })
                .catch((e) => {
                    this.errors.push(e);
                });
        },
    },

    created() {
        this.obtenerPantallas();
    },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->

<style scoped>
.tit-por:hover {
    color: #cbd3da !important;
    font-family: 'Montserrat';
    font-weight: 300;
    letter-spacing: 8px;
    transition: all .3s;
    text-shadow: 0 0 30px #69AAE6
}

.tit-por {
    color: #cbd3da !important;
    font-family: 'Montserrat';
    letter-spacing: 2px;
    text-decoration: none;
    font-weight: 300;
    text-shadow: 0 0 30px #69AAE6
}

.img-pan {
    border: 5px solid transparent;
    width: 250px;
    height: 250px;
    transition: transform .2s;
    transition: all .3s;
    border-radius: 15px;
    border: 15px solid transparent;

}

.img-mapa {
    width: 105%;
    display: block;
    border: #2c3e50 8px solid;
border-radius: 15px;
    margin-right: auto;

}

.p-10 {
    padding: 25%;

}

.img-pan:hover {
    transform: scale(1.2);
    transition: all .3s;
}

.ex-term {
    font-size: 15px;
    text-align: center !important;
}

.img-caract {
    width: 98%;
    border: 3px solid #34495e;
}

.tit-catego {

    color: #cbd3da !important;
    font-family: 'Montserrat';
    letter-spacing: 2px;
    font-weight: 300;
    text-align: right !important;

}

.con-port {
    text-align: center;
    padding: 5%;

}

.logo {
    width: 10%;
}

* {
    box-sizing: border-box;
}

body {
    font-family: "Open Sans";
    line-height: 1.618em;
    background: #2c3e50;
}

.wrapper {
    max-width: 65rem;
    width: 100%;
    margin: 2rem auto;
    padding: 5rem;
    text-align: center;

    border: 0.5rem solid #34495e;
}

hr {
    border: 0;
    border-bottom: 0.0625rem solid #bbb;
    margin: 3rem 0;
}

button {
    font-size: 2em;
    background: #3498db;
    color: #fff;
    border: 0.25rem solid #3498db;
    padding: 0.85em 0.75em;
    margin: 1rem;
    position: relative;
    z-index: 1;
    overflow: hidden;

}

button:hover {
    color: #3498db;
}

button::after {
    content: "";
    background: #ecf0f1;
    position: absolute;
    z-index: -1;
    padding: 0.85em 0.75em;
    display: block;
}

button[class^="slide"]::after {
    transition: all 0.35s;
}

button[class^="slide"]:hover::after {
    left: 0;
    right: 0;
    top: 0;
    bottom: 0;
    transition: all 0.35s;
}

button.slide_from_left::after {
    top: 0;
    bottom: 0;
    left: -100%;
    right: 100%;
}

button.slide_from_right::after {
    top: 0;
    bottom: 0;
    left: 100%;
    right: -100%;
}

button.slide_from_top::after {
    left: 0;
    right: 0;
    top: -100%;
    bottom: 100%;
}

button.slide_from_bottom::after {
    left: 0;
    right: 0;
    top: 100%;
    bottom: -100%;
}

button[class^="grow"]::after {
    transition: all 0.3s ease;
}

button[class^="grow"]:hover::after {
    transition: all 0.3s ease-out;
}

button.grow_box::after {
    left: 0;
    right: 0;
    top: 0;
    bottom: 0;
    transform: scale(0, 0);
}

button.grow_box:hover::after {
    transform: scale(1, 1);
}

button.grow_ellipse::after {
    border-radius: 50%;
    left: -50%;
    right: -50%;
    top: -150%;
    bottom: -150%;
    line-height: 8.34em;
    transform: scale(0, 0);
}

button.grow_ellipse:hover::after {
    transform: scale(1, 1);
}

button.grow_skew_forward::after {
    left: -20%;
    right: -20%;
    top: 0;
    bottom: 0;
    transform: skewX(-45deg) scale(0, 1);
}

button.grow_skew_forward:hover::after {
    transform: skewX(-45deg) scale(1, 1);
}

button.grow_skew_backward::after {
    left: -20%;
    right: -20%;
    top: 0;
    bottom: 0;
    transform: skewX(45deg) scale(0, 1);
}

button.grow_skew_backward:hover::after {
    transform: skewX(45deg) scale(1, 1);
}

button.grow_spin::after {
    left: 0;
    right: 0;
    top: 0;
    bottom: 0;
    transform: scale(0, 0) rotate(-180deg);
}

button.grow_spin:hover::after {
    transform: scale(1, 1) rotate(0deg);
}
</style>
