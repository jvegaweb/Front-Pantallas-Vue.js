<template>
<!-- Todos los proyectos en la pantalla inicial -->
<div class="hello">
    <h1 class="tit-por">Nuestros Proyectos</h1>
    <div class="container">
        <div class="row p-2 p-2">
            <router-link to="/proyecto/1" class="col-lg-3">
                <div class="txt-proyect">EDIFICIO TOWNHOUSES LOS DOMINICOS</div>
                <div class="corner"></div>
                <img class="img-pro" src="img/proyects/12BOX.jpg" alt="">
            </router-link>

            <router-link to="/proyecto/2" class="col-lg-3">
                <div class="txt-proyect">CONDOMINIO TERRALTA CHAMISERO V CHICUREO</div>
                <div class="corner"></div>
                <img class="img-pro" src="img/proyects/11BOX.jpg" alt="">
            </router-link>

            <router-link to="/proyecto/3" class="col-lg-3">
                <div class="txt-proyect">EDIFICIO CASAS DEL PARQUE 8 SAN BERNARDO</div>
                <div class="corner"></div>
                <img class="img-pro" src="img/proyects/10BOX.jpg" alt="">
            </router-link>
            <router-link to="/proyecto/3" class="col-lg-3">
                <div class="txt-proyect">EDIFICIO CASAS DEL PARQUE 7 SAN BERNARDO</div>
                <div class="corner"></div>
                <img class="img-pro" src="img/proyects/10BOX.jpg" alt="">
            </router-link>

            <router-link to="/proyecto/6" class="col-lg-3">
                <div class="txt-proyect">EDIFICIO MILAN 1242 SAN MIGUEL</div>
                <div class="corner"></div>
                <img class="img-pro" src="img/proyects/9BOX.jpg" alt="">
            </router-link>

            <router-link to="/proyecto/" class="col-lg-3">
                <div class="txt-proyect">EDIFICIO LOS LEONES ÑUÑOA</div>
                <div class="corner"></div>
                <img class="img-pro" src="img/proyects/8BOX.jpg" alt="">
            </router-link>

            <router-link to="/proyecto/" class="col-lg-3">
                <div class="txt-proyect">EDIFICIO POCURO PROVIDENCIA</div>
                <div class="corner"></div>
                <img class="img-pro" src="img/proyects/7BOX.jpg" alt="">
            </router-link>

            <router-link to="/proyecto/" class="col-lg-3">
                <div class="txt-proyect">CONDOMINIO LOS ALMENDROS REÑACA</div>
                <div class="corner"></div>
                <img class="img-pro" src="img/proyects/6BOX.jpg" alt="">
            </router-link>

            <router-link to="/proyecto/" class="col-lg-3">
                <div class="txt-proyect">EDIFICIO LAS ACACIAS LA FLORIDA</div>
                <div class="corner"></div>
                <img class="img-pro" src="img/proyects/5BOX.jpg" alt="">
            </router-link>

            <router-link to="/proyecto/" class="col-lg-3">
                <div class="txt-proyect">CASAS HACIENDA CONQUISTADORES P ALTO 2A</div>
                <div class="corner"></div>
                <img class="img-pro" src="img/proyects/4BOX.jpg" alt="">
            </router-link>

            <router-link to="/proyecto/" class="col-lg-3">
                <div class="txt-proyect">CASAS HACIENDA CONQUISTADORES P ALTO 2M</div>
                <div class="corner"></div>
                <img class="img-pro" src="img/proyects/3BOX.jpg" alt="">
            </router-link>

            <router-link to="/proyecto/" class="col-lg-3">
                <div class="txt-proyect">CONDOMINIO TERRALTA LOS DOMINICOS LAS CONDES</div>
                <div class="corner"></div>
                <img class="img-pro" src="img/proyects/2BOX.jpg" alt="">
            </router-link>
        </div>
    </div>
</div>

</template>

<!-- Cierre de Todos los proyectos en la pantalla inicial -->

<script>
export default {
    name: 'Inicio',
    props: {
        msg: String
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->

<style scoped>
.txt-proyect {
    background-color: #E41460 !important;
    color: #FFF;
    text-align: center;
    text-transform: uppercase;
    font-weight: bold;
    min-width: 200px;
    width: 50px;
    height: auto;
    padding: 5px;
    position: absolute;
    top: 4px;
    right: 38px;
    font-size: 10px;
       font-weight: bold;
    border-radius: 3px;

    box-shadow: 0 0 30px #69AAE6;
    
}

@media (max-width: 900px) {
  .txt-proyect {
    background-color: #E41460 !important;
    color: #FFF;
    text-align: center;
    text-transform: uppercase;
    font-weight: bold;
    min-width: 200px;
    width: 100px;
    height: auto;
    padding: 5px;
    position: absolute;
    top: 5px;
    right: 25%;
    font-size: SMALL;
    opacity: 0.9;
    border-radius: 3px;
    border: 1px solid #69AAE6;
    box-shadow: 0 0 30px #69AAE6;
  }
}

.txt-proyect {
    transition: transform .2s;
}

.txt-proyect:hover {
    transform: scale(1.1);
}

.img-pro {
    border: 5px solid transparent;
    border-radius: 15px;
    width: 100%;

}

.tit-por:hover {
    color: #cbd3da !important;
    font-family: 'Montserrat';
    font-weight: 300;
    letter-spacing: 10px;
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

.bg-cuadrof {
    color: #fff;

    font-size: 12px;
    margin-top: 100px;
    border: 1px solid #588CC6;
    opacity: 1;
    width: 100%;
    border-radius: 15px;
}
</style>