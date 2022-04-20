<template>
  <!-- Modal -->
  <div class="container">
    <h2 class="tit-por">GALERIA INTERIOR</h2>
    <carousel
      :responsive="{
        0: { items: 1, nav: false },
        800: { items: 3, nav: false },
      }"
    >
      <div v-for="gallery1 in gallery_1" :key="gallery1.id">
        <img :src="gallery1.media[0].url" height="300px" />
      </div>
    </carousel>
  </div>
</template>

<script>


import axios from 'axios'
import carousel from "vue-owl-carousel";

export default {
    components: {
        carousel,
    },
    props: ['id'],
    data() {

        return {
             proyecto: null,
      proyect: null,
      gallery_1: [],

        }
    },
    methods: {
        obtenerPantallas() {
            var config = {
                method: "get",
                url: `http://127.0.0.1:8000/api/v1/pantallas/${this.$route.params.id}`,
                headers: {
                    Authorization: "Bearer 2|qU95XxrcuQNS4Bb9Vyb3uMlKpZar3jcYP7bXhUvH",
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

.tit-por {

    color: #cbd3da !important;
    font-family: 'Montserrat';
    letter-spacing: 2px;
    text-decoration: none;
    font-weight: 300;
    text-shadow: 0 0 30px #69AAE6
}

html {
  scroll-behavior: smooth;
}
.owl-stage-outer {
  display: flex;
  flex-wrap: nowrap;
  flex-direction: column;
}
.owl-stage-outer > .owl-stage {
  margin: 0 auto;
}


</style>
