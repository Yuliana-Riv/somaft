<template>
  <div id="HeaderSec">
    <div class="dflx">
      <div class="titles">
        <div v-if="historyOption == 'Perzonalizacion'">
          <h3>PERSONALIZACIÓN</h3>
          <p>Selección de Perfiles de Color</p>
        </div>

        <div v-else-if="historyOption == 'Usuarios'">
          <div v-if="historyOptionUsr == 'Default'">
            <h3>USUARIOS</h3>
            <p>Accesos permitidos al administrador</p>
          </div>
          <div v-if="historyOptionUsr == 'Add'">
            <h3>USUARIOS</h3>
            <p>Agregar nuevo usuario</p>
          </div>
          <div v-if="historyOptionUsr == 'Edit'">
            <h3>USUARIOS</h3>
            <p>Editar usuario</p>
          </div>
        </div>
        <div v-else-if="historyOption == 'Personalizacion'">
          <div v-if="historyOptionPrf == 'Default'">
            <h3>PERSONALIZACIÓN</h3>
            <p>Selección de Perfiles de Color</p>
          </div>
          <div v-if="historyOptionPrf == 'Add'">
            <h3>PERSONALIZACIÓN</h3>
            <p>Agregar color</p>
          </div>
          <div v-if="historyOptionPrf == 'Edit'">
            <h3>PERSONALIZACIÓN</h3>
            <p>Editar color</p>
          </div>
        </div>
        <div v-else-if="historyOption == 'Default'">
          <div v-if="historyOptionUsr == 'Default'">
            <h3>USUARIOS</h3>
            <p>Accesos permitidos al administrador</p>
          </div>
          <div v-if="historyOptionUsr == 'Add'">
            <h3>USUARIOS</h3>
            <p>Agregar nuevo usuario</p>
          </div>
          <div v-if="historyOptionUsr == 'Edit'">
            <h3>USUARIOS</h3>
            <p>Editar usuario</p>
          </div>
        </div>

        <div v-else-if="historyOption == 'colaborador'">
          <div v-if="historyOptionClb == 'Default'">
            <h3>COLABORADORES</h3>
            <p>Listado de colaboradores</p>
          </div>
          <div v-if="historyOptionClb == 'Add'">
            <h3>COLABORADORES</h3>
            <p>Agregar nuevo colaborador</p>
          </div>
          <div v-if="historyOptionClb == 'Edit'">
            <h3>COLABORADORES</h3>
            <p>Editar colaborador</p>
          </div>
        </div>

        <div v-else-if="historyOption == 'terrenos'">
          <div v-if="historyOptionTrr == 'Default'">
            <h3>TERRENOS</h3>
            <p>Listado de terrenos</p>
          </div>
          <div v-if="historyOptionTrr == 'Add'">
            <h3>TERRENOS</h3>
            <p>Agregar nuevo terreno</p>
          </div>
          <div v-if="historyOptionTrr == 'Edit'">
            <h3>TERRENOS</h3>
            <p>Editar terreno</p>
          </div>
        </div>

        <div v-else-if="historyOption == 'casas'">
          <div v-if="historyOptionCss == 'Default'">
            <h3>CASAS</h3>
            <p>Listado de casas</p>
          </div>
          <div v-if="historyOptionCss == 'Add'">
            <h3>CASAS</h3>
            <p>Agregar nuevo casa</p>
          </div>
          <div v-if="historyOptionCss == 'Edit'">
            <h3>CASAS</h3>
            <p>Editar casa</p>
          </div>
        </div>
        <div v-else-if="historyOption == 'oficinas'">
          <div v-if="historyOptionOfn == 'Default'">
            <h3>OFICINAS</h3>
            <p>Listado de oficinas</p>
          </div>
          <div v-if="historyOptionOfn == 'Add'">
            <h3>OFICINAS</h3>
            <p>Agregar nuevo oficina</p>
          </div>
          <div v-if="historyOptionOfn == 'Edit'">
            <h3>OFICINAS</h3>
            <p>Editar oficina</p>
          </div>
        </div>
        <div v-else-if="historyOption == 'locales'">
          <div v-if="historyOptionLcl == 'Default'">
            <h3>LOCALES</h3>
            <p>Listado de locales</p>
          </div>
          <div v-if="historyOptionLcl == 'Add'">
            <h3>LOCALES</h3>
            <p>Agregar nuevo local</p>
          </div>
          <div v-if="historyOptionLcl == 'Edit'">
            <h3>LOCALES</h3>
            <p>Editar local</p>
          </div>
        </div>
        <div v-else-if="historyOption == 'nave'">
          <div v-if="historyOptionNv == 'Default'">
            <h3>NAVES INDUSTRIALES</h3>
            <p>Listado de naves</p>
          </div>
          <div v-if="historyOptionNv == 'Add'">
            <h3>NAVES INDUSTRIALES</h3>
            <p>Agregar nueva nave</p>
          </div>
          <div v-if="historyOptionNv == 'Edit'">
            <h3>NAVES INDUSTRIALES</h3>
            <p>Editar nave</p>
          </div>
        </div> 
        <div v-else-if="historyOption == 'bodega'">
          <div v-if="historyOptionBod == 'Default'">
            <h3>BODEGA</h3>
            <p>Listado de bodega</p>
          </div>
          <div v-if="historyOptionBod == 'Add'">
            <h3>BODEGA</h3>
            <p>Agregar nuevo bodega</p>
          </div>
          <div v-if="historyOptionBod == 'Edit'">
            <h3>BODEGA</h3>
            <p>Editar bodega</p>
          </div>
        </div>
        <div v-else-if="historyOption == 'otros'">
          <div v-if="historyOptionOtr == 'Default'">
            <h3>OTROS</h3>
            <p>Listado de otros</p>
          </div>
          <div v-if="historyOptionOtr == 'Add'">
            <h3>OTROS</h3>
            <p>Agregar nuevo item</p>
          </div>
          <div v-if="historyOptionOtr == 'Edit'">
            <h3>OTROS</h3>
            <p>Editar item</p>
          </div>
        </div>
        <div v-else-if="historyOption == 'suscripciones'">
          <div v-if="historyOptionSbs == 'Default'">
            <h3>SUSCRIPCIONES</h3>
            <p>Listado de locales</p>
          </div>
          <div v-if="historyOptionSbs == 'Add'">
            <h3>SUSCRIPCIONES</h3>
            <p>Agregar nuevo local</p>
          </div>
          <div v-if="historyOptionSbs == 'Edit'">
            <h3>SUSCRIPCIONES</h3>
            <p>Editar local</p>
          </div>
        </div>

        <div v-else-if="historyOption == 'Banner'">
          <div v-if="historyOptionBnr == 'Default'">
            <h3>BANNER</h3>
            <p>Lista disponibles</p>
          </div>
          <div v-if="historyOptionBnr == 'Add'">
            <h3>BANNER</h3>
            <p>Agregar nueva</p>
          </div> 
        </div> 

        <div v-else-if="historyOption == 'direccion'">
          <div v-if="historyOptionAdr == 'Default'">
            <h3>DIRECCIÓN</h3>
            <p>Lista disponibles</p>
          </div>
          <div v-if="historyOptionAdr == 'Add'">
            <h3>DIRECCIÓN</h3>
            <p>Agregar nueva</p>
          </div> 
          <div v-if="historyOptionAdr == 'Edit'">
            <h3>DIRECCIÓN</h3>
            <p>Editar dirección</p>
          </div>
        </div>

        <div v-else-if="historyOption == 'horario'">
          <div v-if="historyOptionHor == 'Default'">
            <h3>HORARIO</h3>
            <p>Lista disponibles</p>
          </div>
          <div v-if="historyOptionHor == 'Add'">
            <h3>HORARIO</h3>
            <p>Agregar nueva</p>
          </div> 
          <div v-if="historyOptionHor == 'Edit'">
            <h3>HORARIO</h3>
            <p>Editar horario</p>
          </div>
        </div>

        <div v-else-if="historyOption == 'telefono'">
          <div v-if="historyOptionPho == 'Default'">
            <h3>TELÉFONO</h3>
            <p>Lista disponibles</p>
          </div>
          <div v-if="historyOptionPho == 'Add'">
            <h3>TELÉFONO</h3>
            <p>Agregar nueva</p>
          </div> 
          <div v-if="historyOptionPho == 'Edit'">
            <h3>TELÉFONO</h3>
            <p>Editar teléfono</p>
          </div>
        </div>

        <div v-else-if="historyOption == 'redes-sociales'">
          <div v-if="historyOptionSM == 'Default'">
            <h3>REDES SOCIALES</h3>
            <p>Lista disponibles</p>
          </div>
          <div v-if="historyOptionSM == 'Add'">
            <h3>REDES SOCIALES</h3>
            <p>Agregar nueva</p>
          </div> 
          <div v-if="historyOptionSM == 'Edit'">
            <h3>REDES SOCIALES</h3>
            <p>Editar red social</p>
          </div>
        </div>

        <div v-else>
          <h3>{{ historyOption }}</h3>
          <p>Opción aun no disponible.</p>
        </div>
      </div>
      <div class="user-dv dflx">
        <div>
          <h4>
            {{ identity.name | splitUp }} {{ identity.lastname | splitUp }}
          </h4>
          <button @click="cerrarSesion()">Cerrar Sesión</button>
        </div>
        <div v-if="statusicon == 'success'" class="icon-user">
          <img :src="this.srcImg(icon)" alt="icono usuario" />
        </div>
        <div v-else class="icon-user">
          <img :src="icondefault" alt="icono usuario" />
        </div>
      </div>
    </div>

    <hr class="hrhd" />

    <div v-if="viewModal" class="modal_view">
      <div id="modal_logout">
        <div class="body">
          <img src="../assets/default/logout.png" alt="icono alerta" />
          <h3><span>Cerrar Sesión</span></h3>
        </div>

        <div class="modal_log_btns dflx">
          <p @click="logout()">Aceptar</p>
          <p @click="cancelar()">Cancelar</p>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import { url } from "../global/index";
import { mapActions } from "vuex";
import icondefault from "../assets/default/icon-user.png";
export default {
  name: "HeaderSec",
  data() {
    return {
      message: "",
      status: "",
      viewModal: false,
      url: url,
      icondefault: icondefault,
      statusimg: "success",
    };
  },
  async created() {
    await this.getIdentity();

    let payload = {
      id: this.identity.sub,
      option: "user",
    };
    this.getImage(payload);
  },
  computed: {
    historyOption() {
      return this.$store.getters["main/getHistoryOption"];
    },
    icon() {
      return this.$store.getters["main/img"];
    },
    statusicon() {
      return this.$store.getters["main/statusimg"];
    },
    historyOptionUsr() {
      return this.$store.getters["usuarios/getHistoryOption"];
    },

    historyOptionPrf() {
      return this.$store.getters["profile/getHistoryOption"];
    },
    historyOptionClb() {
      return this.$store.getters["colaborador/getHistoryOption"];
    },
    historyOptionTrr() {
      return this.$store.getters["terrenos/getHistoryOption"];
    },
    historyOptionCss() {
      return this.$store.getters["casas/getHistoryOption"];
    },
    historyOptionOfn() {
      return this.$store.getters["oficinas/getHistoryOption"];
    },

    historyOptionLcl() {
      return this.$store.getters["locales/getHistoryOption"];
    },
    historyOptionNv() {
      return this.$store.getters["nave/getHistoryOption"];
    },
    historyOptionInd() {
      return this.$store.getters["industrial/getHistoryOption"];
    },
    historyOptionOtr() {
      return this.$store.getters["otros/getHistoryOption"];
    },
    historyOptionBod() {
      return this.$store.getters["bodega/getHistoryOption"];
    },
    historyOptionSbs() {
      return this.$store.getters["suscripciones/getHistoryOption"];
    },
    historyOptionBnr() {
      return this.$store.getters["banner/getHistoryOption"];
    },

    historyOptionAdr() {
      return this.$store.getters["address/getHistoryOption"];
    },
    historyOptionHor() {
      return this.$store.getters["horario/getHistoryOption"];
    }, 
    historyOptionPho() {
      return this.$store.getters["phone/getHistoryOption"];
    }, 
    historyOptionSM() {
      return this.$store.getters["social_media/getHistoryOption"];
    },



    identity() {
      return this.$store.getters["admin/getIdentity"];
    },
  },
  methods: {
    ...mapActions("main", ["getImage"]),
    wait: function () {
      setTimeout(() => this.$router.go(), 200);
    },

    getIdentity: async function () {
      let response = await this.$store.dispatch("admin/getData");
      return response;
    },

    cerrarSesion() {
      this.viewModal = true;
    },
    cancelar() {
      this.viewModal = false;
    },
    logout: async function () {
      let response = await this.$store.dispatch("admin/logout");
      this.wait();
    },

    srcImg: function (img) {
      let src = `${url}/user-img/${img}`;

      this.status_img(img);

      return src;
    },

    status_img: async function (img) {
      let payload = {
        option: "user",
        image: img,
      };
      let response = "";

      try {
        response = await this.$store.dispatch("main/getStatusImage", payload);
        if (response.data.status == "error") {
          this.statusimg = "error";
        } else {
          this.statusimg = "success";
        }
      } catch (err) {
        this.statusimg = "error";
      }
    },
  },
  filters: {
    split: (value) => {
      if (!value) return "";
      value = value.toString();

      return value.charAt(0).toUpperCase();
    },
    splitUp: (value) => {
      if (!value) return "";
      value = value.toString();

      let splitStr = value.toLowerCase().split(" ");

      return splitStr[0].charAt(0).toUpperCase() + splitStr[0].substring(1);
    },
    splitName: (value) => {
      if (!value) return "";
      value = value.toString();

      let splitStr = value.toLowerCase().split(" ");
      let len = splitStr.length;

      if (len == 1) {
        return splitStr[0].charAt(0).toUpperCase() + splitStr[0].substring(1);
      }

      return (
        splitStr[0].charAt(0).toUpperCase() +
        splitStr[0].substring(1) +
        " " +
        splitStr[1].charAt(0).toUpperCase() +
        splitStr[1].substring(1)
      );
    },
  },
};
</script>

<style scoped>
#HeaderSec {
  margin-top: 5.46875vw;
}

hr.hrhd {
  width: 70.72916666666667vw;
  margin-left: 0px;
  /*border-bottom: .1px solid #B1B1B1;*/
  margin-top: 1.6145833333333335vw;
  margin-bottom: 1vw;
}

.titles {
  width: 39.375vw;
}
.titles h3 {
  color: var(--color-2);
  font-weight: 600;
  font-size: 1.3020833333333335vw;
  margin: 0vw;
}
.titles p {
  color: var(--color-3);
  margin: 0px;
  font-size: 0.8333333333333334vw;
}

.user-dv {
  margin-left: 10vw;
}

.user-dv h4 {
  color: var(--color-2);
  margin: 0vw;
  font-size: 0.9375vw;
  margin-top: 0.5vw;
  text-align: right;
}
.user-dv button {
  color: var(--color-1);
  text-decoration: underline;
  background: none;
  border: none;
  cursor: pointer;
  font-size: 0.7291666666666666vw;
  margin-left: 3.2vw;
  padding: 0vw;
}
.icon-user {
  margin-left: 0.8854166666666666vw;
  width: 3.6458333333333335vw;
  height: 3.6458333333333335vw;
  overflow: hidden;
  border-radius: 2vw;
}
.icon-user img {
  width: 3.6458333333333335vw;
  height: 3.6458333333333335vw;
}
</style>
