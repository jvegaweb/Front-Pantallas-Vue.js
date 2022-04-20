<template>
<!-- Modal -->
<carousel>
        <img  v-for="gallery2 in gallery_2" :key="gallery2" :src="gallery2.img_gallery_adic.url" />
        
      </carousel>
</template>

<script>

import axios from 'axios'
import carousel from 'vue-owl-carousel'

export default {
    components: {
        carousel
    },
    props: ['id'],
    data() {

        return {
             proyecto: null,
      proyect: null,
            gallery_2: [],

        }
    },
    methods: {
        obtenerGaleria2() {
            const id_proyecto = this.id

            const config = {
                method: "get",
                url: `http://127.0.0.1:8001/api/v1/proyectos/${id_proyecto}`,
                headers: {
                    Authorization: "Bearer 1|QiuFr6l69Kbd4H42FsukJ8bFrW62FlvLRpDQFkMv",
                },
            };

          axios(config)
                .then((response) => {
                    //traemos todos los datos de todos de la pantalla
                    console.log(JSON.parse(JSON.stringify(response.data)));
                    // traemos todos los datos de pantalla especifico segun URL

                    this.proyecto = JSON.parse(JSON.stringify(response.data.data));

                    // traemos la galeria interior

                    this.gallery_1 = JSON.parse(
                        JSON.stringify(response.data.data.gallery_1s)
                    );
                    // traemos la galeria espacios comunes
                    this.gallery_2 = JSON.parse(
                        JSON.stringify(response.data.data.gallery_2s)
                    );

                })
                .catch((e) => {
                    this.errors.push(e);
                });
        },
    },

    created() {
        this.obtenerGaleria2();
    },
};
</script>

<style scoped>
.tit-por {

    color: #cbd3da !important;
    font-family: 'Montserrat';
    letter-spacing: 2px;
    text-decoration: none;
    font-weight: 300;
    text-shadow: 0 0 30px #69AAE6
}
</style>
