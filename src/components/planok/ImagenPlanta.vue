<template>
  <img ref="image" :src="blobUrl" @load="loaded" />
</template>

<script>
import axios from "axios";

/**
 * Load an image url as a blob
 */
async function load(valor) {
  const config = {
    method: "get",
    responseType: "blob",
    url: `https://api-gci-rest.integracionplanok.io/api/modelos/${valor}/imagenes/1`,
    headers: {
      "Content-Type": "image/jpeg",
      Authorization:
        "Bearer eyJhbGciOiJSUzI1NiIsInR5cCI6IkpXVCJ9.eyJwYXlsb2FkIjp7InVzZXJuYW1lIjoyNTk4NTI2MSwiaW5tb2JpbGlhcmlhIjp7ImJkIjoiZ2NpX2Jlc2FsY28iLCJ1cmwiOiJiZXNhbGNvLmNvbWVyY2lhbGlubW9iaWxpYXJpYXMuY2wifX0sImlhdCI6MTYzMDAwODkwNn0.NmV0sqYxvZTLmHh_hMNGbuhnx5hYlbu0IaT1FhQajQK8LKdrQWahDVQTFOxVTuvfUnY2bvBg4hADCAs9UMSndElXOApm6MX67zeXDgj-BB0RI-Dvb-5D3tS5DSFK3EuWKY8SylDDZWPHbV4TIpZkV70UEAPZ32Y7Yma8M3EBQbCulaUgJTH2y-MGqUlDf7Ey8KmgT4N8G9Mwx7WFJdpNTMVIad52Gw1yA_Gt56FYLNyuEGfzffkYPtMhLEa1k_2smjBxECT9-gcufAlXzDbgXN-QSfFQmZrVMm-IztYzB6zGSjOgp8agWqfSVrKP53Fup_AL77tEWbMqK1tXmVmhIg",
    },
  };
  const response = await axios.request(config);
  return response.data; // the blob
}

/**
 * Loads the image as a blob and createObjectURL().
 * Set the img tag's src to the object url.
 * Once the image is loaded, revoke the object url (avoid memory leak).
 * Notice that the page can still show the image, but the src blob is no longer valid.
 */
export default {
  data() {
    return {
      blobUrl: null,
    };
  },

  props: {
    valor: {
      type: Number,
    },
  },

  methods: {
    loaded() {
      if (this.blobUrl) URL.revokeObjectURL(this.blobUrl);
    },
  },

  watch: {
    valor: {
      immediate: true,
      handler(valor) {
        if (!valor) return;
        load(valor).then((blob) => {
          this.blobUrl = URL.createObjectURL(blob);
        });
      },
    },
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
</style>
