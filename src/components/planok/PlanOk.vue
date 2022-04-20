<template>
  <div class="container">
    <div class="row justify-content-md-center">
      <div
        class="col-lg-4 p-2"
        v-for="modelo in displayedModelos"
        :key="modelo.id"
      >
        <div id="plan" class="card">
          <div class="plan card-header">
            <h3 class="tt-card">{{ modelo.nombre }}</h3>
          </div>

          <ImagenPlanta :valor="modelo.id" width="100%"></ImagenPlanta>
          <div class="card-footer">
            <div class="row">
             
            
              <div class="col-lg-6">
                <!-- BTN COTIZAR-->
               

                <!-- Modal -->
                <div
                  class="modal fade"
                  id="exampleModal"
                  tabindex="-1"
                  aria-labelledby="exampleModalLabel"
                  aria-hidden="true"
                >
                  <div class="modal-dialog modal-xl">
                    <div class="modal-content">
                      <div class="modal-body">
                        <div class="row">
                          <div class="col-lg-5 pb-4">
                            <FormCotizar
                              :Mediollegada="MedioLlegada"
                              class="mt-4"
                              :valor="modelo.id"
                            />
                            <p class="text-pe">INTEGRACIÓN CGI PLAN OK 
                            <img width="24px" src="https://www.planok.com/wp-content/uploads/2019/10/PlanOK-Logos-fondo_0005_Vector-Smart-Object-100x100.png" alt="">
                          </p></div>

                          <div class="col-lg-7">
                            <ImagenPlanta
                              :valor="modelo.id"
                              width="100%"
                            ></ImagenPlanta>
                          </div>
                        </div>
                      </div>
                    </div>
                  </div>
                </div>

                <div></div>
              </div>
            </div>
          </div>
        </div>
      </div>

     <div class="col-lg-12">
        <button
          type="button"
          class="btn btn-pagination"
          v-if="page != 1"
          @click="page--"
        >
        <
          <i class="bi bi-chevron-left"></i>
        </button>
        <button
          type="button"
          class="btn btn-pagination"
          v-for="pageNumber in pages.slice(page - 1, page + 5)"
          :key="pageNumber"
          @click="page = pageNumber"
        >
          {{ pageNumber }}
        </button>
        <button
          type="button"
          class="btn btn-pagination"
          v-if="page < pages.length"
          @click="page++"
         
        >
         >
          <i class="bi bi-chevron-right"></i>
        </button>
      </div>
    </div>
  </div>

</template>

<script>
import axios from "axios";
import FormCotizar from "../planok/FormCotizar.vue";
import ImagenPlanta from "../planok/ImagenPlanta.vue";

export default {
  props: ["id"],
  components: {
    ImagenPlanta,
    FormCotizar,
  },
  data() {
    return {
      modelos: [],
      page: 1,
      perPage: 3,
      pages: [],
      MedioLlegada: 0,
    };
  },
  created() {
    this.getModelos();
    this.getMediollegada();
  },

  methods: {
    getMediollegada() {
      const config = {
        method: "get",
        url: `https://api-gci-rest.integracionplanok.io/api/proyectos/${this.id}/mediosDeLlegada`,
        headers: {
          Accept: "application/json",
          Authorization:
            "Bearer eyJhbGciOiJSUzI1NiIsInR5cCI6IkpXVCJ9.eyJwYXlsb2FkIjp7InVzZXJuYW1lIjoyNTk4NTI2MSwiaW5tb2JpbGlhcmlhIjp7ImJkIjoiZ2NpX2Jlc2FsY28iLCJ1cmwiOiJiZXNhbGNvLmNvbWVyY2lhbGlubW9iaWxpYXJpYXMuY2wifX0sImlhdCI6MTYzMDAwODkwNn0.NmV0sqYxvZTLmHh_hMNGbuhnx5hYlbu0IaT1FhQajQK8LKdrQWahDVQTFOxVTuvfUnY2bvBg4hADCAs9UMSndElXOApm6MX67zeXDgj-BB0RI-Dvb-5D3tS5DSFK3EuWKY8SylDDZWPHbV4TIpZkV70UEAPZ32Y7Yma8M3EBQbCulaUgJTH2y-MGqUlDf7Ey8KmgT4N8G9Mwx7WFJdpNTMVIad52Gw1yA_Gt56FYLNyuEGfzffkYPtMhLEa1k_2smjBxECT9-gcufAlXzDbgXN-QSfFQmZrVMm-IztYzB6zGSjOgp8agWqfSVrKP53Fup_AL77tEWbMqK1tXmVmhIg",
        },
      };

      axios(config)
        .then((response) => {
          // JSON responses are automatically parsed.
          this.MedioLlegada = response.data[3].id;
          console.log(response.data[3].id);
        })
        .catch((e) => {
          this.errors.push(e);
        });
    },

    getModelos() {
      const ids = this.id;
      const config = {
        method: "get",
        url: `https://api-gci-rest.integracionplanok.io/api/proyectos/${ids}/modelos`,
        headers: {
          Accept: "application/json",
          Authorization:
            "Bearer eyJhbGciOiJSUzI1NiIsInR5cCI6IkpXVCJ9.eyJwYXlsb2FkIjp7InVzZXJuYW1lIjoyNTk4NTI2MSwiaW5tb2JpbGlhcmlhIjp7ImJkIjoiZ2NpX2Jlc2FsY28iLCJ1cmwiOiJiZXNhbGNvLmNvbWVyY2lhbGlubW9iaWxpYXJpYXMuY2wifX0sImlhdCI6MTYzMDAwODkwNn0.NmV0sqYxvZTLmHh_hMNGbuhnx5hYlbu0IaT1FhQajQK8LKdrQWahDVQTFOxVTuvfUnY2bvBg4hADCAs9UMSndElXOApm6MX67zeXDgj-BB0RI-Dvb-5D3tS5DSFK3EuWKY8SylDDZWPHbV4TIpZkV70UEAPZ32Y7Yma8M3EBQbCulaUgJTH2y-MGqUlDf7Ey8KmgT4N8G9Mwx7WFJdpNTMVIad52Gw1yA_Gt56FYLNyuEGfzffkYPtMhLEa1k_2smjBxECT9-gcufAlXzDbgXN-QSfFQmZrVMm-IztYzB6zGSjOgp8agWqfSVrKP53Fup_AL77tEWbMqK1tXmVmhIg",
        },
      };

      axios(config)
        .then((response) => {
          // JSON responses are automatically parsed.
          this.modelos = response.data;
          console.log(response.data);
        })
        .catch((e) => {
          this.errors.push(e);
        });
    },

    setModelos: function () {
      const numberOfPages = Math.ceil(this.modelos.length / this.perPage);
      for (let i = 1; i <= numberOfPages; i++) this.pages.push(i);
    },

    paginate: function (modelos) {
      const page = this.page;
      const perPage = this.perPage;
      const from = page * perPage - perPage;
      const to = page * perPage;
      return modelos.slice(from, to);
    },
  },
  computed: {
    displayedModelos: function () {
      return this.paginate(this.modelos);
    },
  },
  watch: {
    modelos() {
      this.setModelos();
    },
  },
};
</script>

<style scoped>
.card {
  border: solid 1px #00326a;
  background-color: #06142a;

  color: #fff;
}

.bor-right {
  border-right: solid 1px #00326a;
}

.tt-card {
  color: #04bca7;
}

.btn-rosa {
  margin-top: 10px;
  background-color: #ce20ce;
  color: #fff;
}

.btn-rosa:hover {
  background-color: #b323b3;
  color: #fff;
}

.modal-content {
  background-color: #06142a;
}

.modal-footer {
  border: none;
}

.text-pe {
  margin-top: 60px;
  font-size: 8px;
}

.btn-pagination {
  background-color: #264b71;
  color: #fff;
  margin: 1px;
}

.btn-pagination:hover {
  background-color: #04bca7;
}

.btn-pagination:active {
  background-color: #04bca7;
}

.btn-pagination::selection {
  background-color: #04bca7;
}

.border-modal {
  border: solid 1px #5094cf;
  border-radius: 5px;
}

.prices {
  color: #5094cf;
  font-size: 21px;
}

.rosa-desde {
  color: #b323b3;
  font-size: 8px;
}

.miniprice {
  color: #b323b3;
  font-size: 8px;
}
</style>
