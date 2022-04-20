<template>
<div class="forms">
    <div v-show="alertError == true" class="alert alert-danger" role="alert">
        <h4 class="alert-heading">PROBLEMAS AL COTIZAR</h4>
        <p>Ingresaste mal el rut por favor corregir.</p>
        <p class="mb-0"></p>
    </div>

    <!-- FASE 1 de VALIDACION -->
    <div  v-show="ocultarPreguntas == true">
        <h4 class="pl-1 tt-pr">Bienvenido</h4>
        <h5 class="pl-1 tt-p">A NUESTRO COTIZADOR</h5>
        <p class="pl-1 tt-pp">
            Para poder cotizar online, debemos saber si antes ya haz cotizado en nuestra plataforma.
        </p>
        <hr />
        <div class="row">
            <div class="col-lg-6 ">
                <input type="radio" id="radio"  v-model="checked" class="cheking"  value="1" />
                <label for="checkbox" class="txt-pregunta">Si he cotizado </label>
            </div>
            <div class="col-lg-6 ">
                <input type="radio" name="radio" id="radio" class="cheking"  v-model="checked" value="2" />
                <label for="checkbox" class="txt-pregunta">Primera vez cotizando</label>
            </div>
        </div>
        <hr />
    </div>
    <!-- FASE 1 de VALIDACION -->

    <!-- SI YA ESTA REGISTRADO BUSCAMOS SUS DATOS -->
    <form v-show="checked == 1" v-on:submit.prevent="consultarContacto()">
        <hr />
        <span class="txt-lead-rosa">Ingresa tu rut en formato solicitado</span>
        <label for="rut">
            <div class="row">
                <div class="col-lg-8 mb-2">
                    <input type="number" maxlength="8" oninput="if(this.value.length > this.maxLength) this.value = this.value.slice(0, this.maxLength);" name="rut" ref="form.rut" v-model="form.rut" class="form-control" placeholder="Rut..." />
                </div>
                <div class="col-lg-4 mb-2">
                    <input type="text" name="dv" v-model="form.dv" ref="form.dv" class="form-control" placeholder="Digito" />
                </div>
            </div>
        </label>
        <div class="col-lg-12 text-right mt-4">
            <button type="button" class="btn btn-rosa mr-2" data-dismiss="modal">
                Cerrar
            </button>
            <button class="btn btn-celeste">Siguiente</button>
        </div>
    </form>

    <!-- SELECCIONAR UNIDAD  -->
    <form v-show="selectUnidad == true" v-on:submit.prevent="crearCotizacionValidados()">
        <hr />

        <span class="txt-lead-rosa">Nombre completo:</span> {{ user.nombre }}
        <br />
        <span class="txt-lead-rosa"> RUT: </span>{{ user.dni }} <br />
        <span class="txt-lead-rosa"> Email: </span> {{ user.email }}<br />

        <div class="col-lg-12 mt-4">
            <p class="txt-lead-rosa">Debes seleccionar la unidad interesada</p>

            <select id="unidad" v-model="unidadSelecionada" name="unidad" class="form-control">
                <option v-for="unidad in unidades" :key="unidad.id" :value="unidad.id" :v-if="unidad.estado === 'Disponible'">
                    Unidad: {{ unidad.nombre }} - {{ unidad.orientacion }} - Piso:
                    {{ unidad.piso }}
                </option>
            </select>
        </div>

        <div class="col-lg-12 text-right mt-4">
            <button type="button" class="btn btn-rosa mr-2" data-dismiss="modal">
                Cerrar
            </button>
            <button class="btn btn-celeste">Siguiente</button>
        </div>
    </form>

    <!-- SELECCIONAR UNIDAD  -->

    <!-- PREVIEW FINAL COTIZACION -->

    <div v-show="previewFinalValidado == true">
        <span>VISTA PREVIA COTIZACION</span>
        <hr />
        <h5>DATOS CLIENTE</h5>
        <span class="txt-lead-rosa">Nombre completo:</span> {{ user.nombre }}
        <br />
        <span class="txt-lead-rosa"> RUT: </span>{{ user.dni }} <br />
        <span class="txt-lead-rosa"> Email: </span> {{ user.email }}<br />
        <hr />
        <div>
            <h5>DATOS UNIDAD COTIZADA</h5>
            <span class="txt-lead-rosa">Proyecto Inmobiliario: </span>
            {{ uniProyecto }} <br />
            <span class="txt-lead-rosa">Unidad Cotizada: </span> {{ uniNombre }}
            <br />
            <span class="txt-lead-rosa">Habitaciones y Baños: </span>
            {{ uniPrograma }} <br />
            <span class="txt-lead-rosa">Valor en UF: </span> {{ uniPrecio }} <br />
            <span class="txt-lead-rosa">Superficie Total: </span>{{ uniSupTotal }} m²<br />
            <span class="txt-lead-rosa">Superficie Util: </span>{{ uniSupUtil }} m²<br />
            <span class="txt-lead-rosa">Superficie Terraza: </span>{{ uniSupTerra }} m²<br />
        </div>
        <hr />
        <button type="button" class="btn btn-danger mr-2" data-dismiss="modal">
            Cerrar
        </button>
    </div>

    <!-- PREVIEW FINAL COTIZACION -->

    <!-- SI NO ESTAS REGISTRADO CREAMOS EL USUARIO -->

    <form v-show="checked == 2" v-on:submit.prevent="crearContacto()">
        <label for="rut">
            <div class="row">
                <div class="col-lg-12 mb-2">
                    <input type="text" v-model="form.nombre" ref="form.nombre" name="nombre" class="form-control" placeholder="Nombre" />
                </div>
                <div class="col-lg-12 mb-2">
                    <input type="text" v-model="form.apellidoMaterno" ref="form.apellidoMaterno" name="apellidoMaterno" class="form-control" placeholder="Apellido Materno" />
                </div>
                <div class="col-lg-12 mb-2">
                    <input type="text" v-model="form.apellidoPaterno" ref="form.apellidoPaterno" name="apellidoPaterno" class="form-control" placeholder="Apellido Paterno" />
                </div>
                <div class="col-lg-8 mb-2">
                    <input type="number" maxlength="8" oninput="if(this.value.length > this.maxLength) this.value = this.value.slice(0, this.maxLength);" name="rut" ref="form.rut" v-model="form.rut" class="form-control" placeholder="Rut..." />
                </div>
                <div class="col-lg-4 mb-2">
                    <input type="text" name="dv" v-model="form.dv" ref="form.dv" class="form-control" placeholder="Digito" />
                </div>
                <div class="col-lg-12 mb-2">
                    <input type="number" maxlength="10" oninput="if(this.value.length > this.maxLength) this.value = this.value.slice(0, this.maxLength);" name="telefono" v-model="form.celular" ref="form.celular" class="form-control" placeholder="Telefono" />
                </div>
                <div class="col-lg-12 mb-2">
                    <input type="text" name="email" v-model="form.email" ref="form.email" class="form-control" placeholder="Email" />
                </div>

                <div class="col-lg-12 text-right mt-4">
                    <button type="button" class="btn btn-danger mr-2" data-dismiss="modal">
                        Cerrar
                    </button>
                    <button class="btn btn-rosa">Siguiente</button>
                </div>
            </div>
        </label>
    </form>
    <!-- SI NO ESTAS REGISTRADO CREAMOS EL USUARIO -->
</div>
</template>

<script>
import axios from "axios";

export default {
    data() {
        return {
            checked: null,
            checked2: null,
            unidades: [],
            form: {
                nombre: "",
                rut: 11111111,
                dv: "",
                apellidoPaterno: "",
                apellidoMaterno: "",
                email: "",
                celular: "",
            },
            idUser: "",
            user: [],
            statusUser: "",
            alertError: false,
            validarUser: false,
            selectUnidad: false,
            ocultarPreguntas: true,
            previewFinalValidado: false,
            unidadSelecionada: 0,
            respuesta: null,
            unidadEspecifica: [],
            uniSupTotal: 0,
            uniSupTerra: 0,
            uniNombre: "",
            uniPrecio: 0,
            uniSupUtil: 0,
            uniProyecto: 0,
            uniPrograma: 0,
        };
    },

    props: {
        valor: {
            type: Number,
        },
        Mediollegada: {
            type: Number,
        },
    },

    methods: {
        // funcion para consultar contactos
        consultarContacto() {
            const rut = this.form.rut;
            let consultarUser = {
                method: "get",
                url: `https://api-gci-rest.integracionplanok.io/api/clientes/naturales?identificador-personal=${rut}`,
                headers: {
                    Authorization: "Bearer eyJhbGciOiJSUzI1NiIsInR5cCI6IkpXVCJ9.eyJwYXlsb2FkIjp7InVzZXJuYW1lIjoyNTk4NTI2MSwiaW5tb2JpbGlhcmlhIjp7ImJkIjoiZ2NpX2Jlc2FsY28iLCJ1cmwiOiJiZXNhbGNvLmNvbWVyY2lhbGlubW9iaWxpYXJpYXMuY2wifX0sImlhdCI6MTYzMDAwODkwNn0.NmV0sqYxvZTLmHh_hMNGbuhnx5hYlbu0IaT1FhQajQK8LKdrQWahDVQTFOxVTuvfUnY2bvBg4hADCAs9UMSndElXOApm6MX67zeXDgj-BB0RI-Dvb-5D3tS5DSFK3EuWKY8SylDDZWPHbV4TIpZkV70UEAPZ32Y7Yma8M3EBQbCulaUgJTH2y-MGqUlDf7Ey8KmgT4N8G9Mwx7WFJdpNTMVIad52Gw1yA_Gt56FYLNyuEGfzffkYPtMhLEa1k_2smjBxECT9-gcufAlXzDbgXN-QSfFQmZrVMm-IztYzB6zGSjOgp8agWqfSVrKP53Fup_AL77tEWbMqK1tXmVmhIg",
                },
                timeout: 10000,
            };

            axios(consultarUser)
                .then((response) => {
                    this.idUser = response.data.id;
                    this.user = response.data;
                    this.statusUser = response.status;
                    if (response.status == 200) {
                        (this.selectUnidad = true), (this.alertError = false);
                        (this.checked = false), (this.ocultarPreguntas = false);
                    }
                })
                .catch((error) => {
                    console.log(error.response.status);
                    this.alertError = true;
                });
        },

        // funcion consultar todas las unidades de este modelo especifico
        getUnidades() {
            const valors = this.valor;
            const config = {
                method: "get",
                url: `https://api-gci-rest.integracionplanok.io/api/modelos/${valors}/productos-principales`,
                headers: {
                    Authorization: "Bearer eyJhbGciOiJSUzI1NiIsInR5cCI6IkpXVCJ9.eyJwYXlsb2FkIjp7InVzZXJuYW1lIjoyNTk4NTI2MSwiaW5tb2JpbGlhcmlhIjp7ImJkIjoiZ2NpX2Jlc2FsY28iLCJ1cmwiOiJiZXNhbGNvLmNvbWVyY2lhbGlubW9iaWxpYXJpYXMuY2wifX0sImlhdCI6MTYzMDAwODkwNn0.NmV0sqYxvZTLmHh_hMNGbuhnx5hYlbu0IaT1FhQajQK8LKdrQWahDVQTFOxVTuvfUnY2bvBg4hADCAs9UMSndElXOApm6MX67zeXDgj-BB0RI-Dvb-5D3tS5DSFK3EuWKY8SylDDZWPHbV4TIpZkV70UEAPZ32Y7Yma8M3EBQbCulaUgJTH2y-MGqUlDf7Ey8KmgT4N8G9Mwx7WFJdpNTMVIad52Gw1yA_Gt56FYLNyuEGfzffkYPtMhLEa1k_2smjBxECT9-gcufAlXzDbgXN-QSfFQmZrVMm-IztYzB6zGSjOgp8agWqfSVrKP53Fup_AL77tEWbMqK1tXmVmhIg",
                },
            };

            axios(config)
                .then((response) => {
                    this.unidades = response.data;
                })
                .catch(function (error) {
                    console.log(error);
                });
        },

         // funcion crear cotizacion solo si el usuario ya ha cotizado antes
        crearCotizacionValidados() {
            const hoy = new Date();
            const fecha = hoy.getFullYear() + "-" + (hoy.getMonth() + 2) + "-" + hoy.getDate();
            const fechaString = hoy.toISOString();

            let Cotizacion = JSON.stringify([{
                productoPrincipal: {
                    id: this.unidadSelecionada,
                    descuento: {
                        valor: 0,
                        unidad: "%",
                    },
                },
                productosSecundarios: [],
                productosAdicionales: [],
                idCliente: this.idUser,
                idTipoIVA: 1,
                fecha: fechaString,
                idMedioLlegada: this.Mediollegada,
                telefonoValidado: true,
                evaluacion: {
                    idExpectativa: 2,
                    idRazonDeCompra: 1,
                    fechaRecontacto: fecha,
                    comentario: "Cotizacion desde la web",
                    idCanalADistancia: 11,
                },
                utm: {
                    source: "string",
                    medium: "string",
                    campaign: "string",
                    term: "string",
                    content: "string",
                },
                gclid: "string",
            }, ]);
console.log(Cotizacion)          
            let config = {
                method: "post",
                url: "https://api-gci-rest.integracionplanok.io/api/cotizaciones",
                headers: {
                    Authorization: "Bearer eyJhbGciOiJSUzI1NiIsInR5cCI6IkpXVCJ9.eyJwYXlsb2FkIjp7InVzZXJuYW1lIjoyNTk4NTI2MSwiaW5tb2JpbGlhcmlhIjp7ImJkIjoiZ2NpX2Jlc2FsY28iLCJ1cmwiOiJiZXNhbGNvLmNvbWVyY2lhbGlubW9iaWxpYXJpYXMuY2wifX0sImlhdCI6MTYzMDAwODkwNn0.NmV0sqYxvZTLmHh_hMNGbuhnx5hYlbu0IaT1FhQajQK8LKdrQWahDVQTFOxVTuvfUnY2bvBg4hADCAs9UMSndElXOApm6MX67zeXDgj-BB0RI-Dvb-5D3tS5DSFK3EuWKY8SylDDZWPHbV4TIpZkV70UEAPZ32Y7Yma8M3EBQbCulaUgJTH2y-MGqUlDf7Ey8KmgT4N8G9Mwx7WFJdpNTMVIad52Gw1yA_Gt56FYLNyuEGfzffkYPtMhLEa1k_2smjBxECT9-gcufAlXzDbgXN-QSfFQmZrVMm-IztYzB6zGSjOgp8agWqfSVrKP53Fup_AL77tEWbMqK1tXmVmhIg",
                    "Content-Type": "application/json",
                },
                timeout: 10000,
                data: Cotizacion,
            };
console.log(config)
            axios(config)
                .then((response) => {
                    this.respuesta = JSON.stringify(response.data);
                    this.previewFinalValidado = true;
                    this.selectUnidad = false;
                    this.unidades.forEach((unidad) => {
                        if (unidad.id === this.unidadSelecionada) {
                            (this.uniSupTotal = unidad.superficies.total),
                            (this.uniSupTerra = unidad.superficies.terraza),
                            (this.uniNombre = unidad.nombre),
                            (this.uniPrecio = unidad.precio),
                            (this.uniSupUtil = unidad.superficies.util),
                            (this.uniPrograma = unidad.programa),
                            (this.uniProyecto = unidad.nombreProyecto);
                            console.log(unidad);
                        }
                    });
                })
                .catch((error) => {
                    console.log(error);
                });
        },


        // funcion crear contacto como persona natural
        crearContacto() {
            const rut = Number(this.form.rut);
            let data = {
                identificadorPersonal: rut,
                digitoVerificador: this.form.dv,
                nombre: this.form.nombre,
                apellidoPaterno: this.form.apellidoPaterno,
                apellidoMaterno: this.form.apellidoMaterno,
                celular: this.form.celular,
                email: this.form.email,
            };

            let config = {
                method: "post",
                url: "https://api-gci-rest.integracionplanok.io/api/clientes/naturales",
                headers: {
                    Authorization: "Bearer eyJhbGciOiJSUzI1NiIsInR5cCI6IkpXVCJ9.eyJwYXlsb2FkIjp7InVzZXJuYW1lIjoyNTk4NTI2MSwiaW5tb2JpbGlhcmlhIjp7ImJkIjoiZ2NpX2Jlc2FsY28iLCJ1cmwiOiJiZXNhbGNvLmNvbWVyY2lhbGlubW9iaWxpYXJpYXMuY2wifX0sImlhdCI6MTYzMDAwODkwNn0.NmV0sqYxvZTLmHh_hMNGbuhnx5hYlbu0IaT1FhQajQK8LKdrQWahDVQTFOxVTuvfUnY2bvBg4hADCAs9UMSndElXOApm6MX67zeXDgj-BB0RI-Dvb-5D3tS5DSFK3EuWKY8SylDDZWPHbV4TIpZkV70UEAPZ32Y7Yma8M3EBQbCulaUgJTH2y-MGqUlDf7Ey8KmgT4N8G9Mwx7WFJdpNTMVIad52Gw1yA_Gt56FYLNyuEGfzffkYPtMhLEa1k_2smjBxECT9-gcufAlXzDbgXN-QSfFQmZrVMm-IztYzB6zGSjOgp8agWqfSVrKP53Fup_AL77tEWbMqK1tXmVmhIg",
                    "Content-Type": "application/json",
                },
                timeout: 10000,
                data: data,
            };

            axios(config)
                .then((response) => {
                    console.log(JSON.stringify(response.data));
                    this.idUser = response.data.id;
                    this.user = response.data;
                    this.statusUser = response.status;

                    this.selectUnidad = true;
                    this.checked = false;
                    this.ocultarPreguntas = false;
                })
                .catch((error) => {
                    console.log(error);
                    this.alertError = true;
                });
        },
    },
    created() {
        // cargar unidades antes de renderizar
        this.getUnidades();
    },
};
</script>

<style scoped>
.card {
    border: solid 1px #e41460;
    background-color: #06142a;
    padding: 10px;
    color: #fff;
}

.btn-rosa {
    background-color: #e41460;
    color: #fff;
}

.btn-rosa:hover {
    background-color: #d11255;
    color: #fff;
}

.modal-content {
    background-color: #06142a;
}

.modal-footer {
    border: none;
}

.txt-lead-rosa {
    color: #04BCA7;
    font-size: 12px;
    font-weight: 600;
    text-align: left;
    font-family: "Montserrat", sans-serif;
}

.text-sm {
    font-size: 11px;
}

.tt-pr{
  color: #CE20CE;
  font-weight: bold;
  text-align: left;
  font-size:28px;
}
.tt-p{
  font-weight: lighter;
  color:#fff;
    text-align: left;
    font-size:20px;
}
.tt-pp{
  font-size:10px;
  text-align: left;
  font-weight: lighter;

}

.txt-pregunta{
  font-size:16px;
  text-align: left;
  margin-left:15px;
  font-weight: lighter;
  font-family: "Montserrat", sans-serif;
}
.cheking{
    background-color: #06142a;
}

.btn-celeste{
    background-color: #04BCA7;
    color:#fff
}
.btn-celeste:hover{
    background-color: #04BCA7;
    color:#fff
}
</style>
