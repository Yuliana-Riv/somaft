<template>
  <div id="Sections">
    <HeaderSec />
    <div v-if="historyOption == 'Usuarios'">
      <Usuarios />
    </div>
    <div v-if="historyOption == 'Personalizacion'">
      <Perfil />
    </div>
    <div v-if="historyOption == 'colaborador'">
      <Colaboradores />
    </div>
    <div v-if="historyOption == 'terrenos'">
      <Terrenos />
    </div>
    <div v-if="historyOption == 'casas'">
      <Casas />
    </div>
    <div v-if="historyOption == 'oficinas'">
      <Oficinas />
    </div>
    <div v-if="historyOption == 'locales'">
      <Locales />
    </div>
    <div v-if="historyOption == 'nave'">
      <Nave />
    </div> 
    <div v-if="historyOption == 'otros'">
      <Otros />
    </div>
    <div v-if="historyOption == 'bodega'">
      <Bodega />
    </div>
    <div v-if="historyOption == 'suscripciones'">
      <Suscripciones />
    </div>
    <div v-if="historyOption == 'Banner'">
      <Banner />
    </div>
    <div v-if="historyOption == 'direccion'">
      <Address />
    </div>
    <div v-if="historyOption == 'horario'">
      <Horario />
    </div>
    <div v-if="historyOption == 'telefono'">
      <Telefono />
    </div>
    <div v-if="historyOption == 'redes-sociales'">
      <SocialMedia />
    </div>
  </div>
</template>
<script>
import { mapActions } from "vuex";

import HeaderSec from "../components/HeaderSec.vue";
import Usuarios from "../views/usuarios/usuarios.vue";
import Perfil from "../views/profile/profile.vue";
import Colaboradores from "../views/colaboradores/colaboradores.vue";
import Terrenos from "../views/terrenos/terrenos.vue";
import Casas from "../views/casas/casas.vue";
import Oficinas from "../views/oficinas/oficinas.vue";
import Locales from "../views/locales/locales.vue";
import Nave from "../views/nave/nave.vue"; 
import Otros from "../views/otros/otros.vue";
import Bodega from "../views/bodega/bodega.vue";
import Suscripciones from "../views/suscripciones/suscripciones.vue";
import Banner from "../views/banner/banner.vue";
import Address from "../views/address/address.vue";
import Horario from "../views/horario/horario.vue";
import Telefono from "../views/telefono/telefono.vue";
import SocialMedia from "../views/social_media/social_media.vue";
export default {
  name: "Sections",
  components: {
    HeaderSec,
    Usuarios,
    Perfil,
    Colaboradores,
    Terrenos,
    Casas,
    Oficinas,
    Locales,
    Nave, 
    Otros,
    Bodega,
    Banner,
    Suscripciones,
    Address,
    Horario,
    Telefono,
    SocialMedia
  },

  data() {
    return {
      search_value: "",
      status: "",
      message: "",
      option: "Default",
    };
  },
  computed: {
    historyOption() {
      return this.$store.getters["main/getHistoryOption"];
    },
  },
  created() {
    let option = localStorage.getItem("nav");
    if (option != undefined && option != null && option != "") {
      this.option = option;
      this.setHistoryOptionMain(option);
    }
  },
  methods: {
    ...mapActions("main", ["setHistoryOptionMain"]),
    ...mapActions("main", ["getHistoryOption"]),
  },
};
</script>
<style scoped>
#Sections {
  background: var(--color-5);
  min-height: 59.25vw;
  width: 73.177083vw;
  margin-left: 4.166666666666666vw;
}

.proximamente p {
  color: var(--color-1);
  font-weight: 700;
  font-size: 5vw;
  margin-top: 11.5vw;
  margin-left: 15vw;
}
</style>
