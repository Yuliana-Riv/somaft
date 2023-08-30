<template>
  <div class="bloquefooter">
    <div class="fila1footer">
      <div class="colmenu">
        <div class="menufooter">
          <h5>MENÚ</h5>
          <ul>
            <li><a href="/">INICIO</a></li>
            <li><a href="#nosotros">NOSOTROS</a></li>
            <li><a href="#directorio">MENÚ</a></li>
            <li><a href="#servicios">CONTACTO</a></li>
            <li><a href="#contacto">BLOG</a></li>
          </ul>
        </div>
        <img class="imgfoomv" src="../assets/footer/imgfootermv.svg" />
        <img class="imgfoopc" src="../assets/footer/imgfooter.svg" />
      </div>
      <div class="infofooter">
        <h5>INFORMACIÓN</h5>
        <div class="bloqueiff">
          <section v-for="(ad, i) in address" :key="i" v-if="address !== 'No se encontraron coincidencias'">
            <p class="titpif">Dirección</p>
            <p class="txtpif">{{ad.address+' '+ad.colonia}}, {{ad.zip+' '+ad.city}}, {{ad.state}}</p>
          </section>

          <section v-for="(ph, i) in phone" :key="i" v-if="phone !== 'No se encontraron coincidencias'">
            <p class="titpif">
              <br />
              Teléfono
            </p> 
            <a v-if="ph.type == 'OFICINA'" :href="ph.link"><p class="txtpif ultpif">{{ph.phone}}</p></a>
            <a v-if="ph.type == 'CELULAR'" :href="ph.link"><p class="txtpif ultpif">{{ph.phone}}</p></a>
            <a v-if="ph.type == 'WHATSAPP'" :href="ph.link"><p class="txtpif ultpif">{{ph.phone}}</p></a>
          </section>

          <section v-for="(hr, i) in horario" :key="i" v-if="horario !== 'No se encontraron coincidencias'">
            <p class="titpif">Horario</p>
            <p class="hor">{{splitday(hr.start_day)+'-'+splitday(hr.end_day)+hr.start_hour+' a '+hr.end_hour}} </p>
          </section>

          <!--<p class="txtpif ultpif last">Domingo – 11:00 am a 6:00 pm</p>-->
        </div>
        <div class="redesfooter" v-if="social_media !== 'No se encontraron coincidencias'">
          <a v-for="(sm,i) in social_media" :key="i" :href="sm.link" target="_blank" rel="noopener noreferrer" 
            ><img src="../assets/navigator/FB.svg" alt="Icono Facebook" v-if="sm.social_media == 'FACEBOOK'"
          /> <img src="../assets/navigator/IG.svg" alt="Icono Instagram" v-if="sm.social_media == 'INSTAGRAM'"
          /> <img src="../assets/navigator/TW.svg" alt="Icono Twitter" v-if="sm.social_media == 'TWITTER'"
          /> <img src="../assets/navigator/WA.svg" alt="Icono Whatsapp" v-if="sm.social_media == 'WHATSAPP'"
          /> <img src="../assets/navigator/TT.svg" alt="Icono Tiktok" v-if="sm.social_media == 'TIKTOK'"
          /> <img src="../assets/navigator/LN.svg" alt="Icono Linkedin" v-if="sm.social_media == 'LINKEDIN'"
          /> <img src="../assets/navigator/YT.svg" alt="Icono Youtube" v-if="sm.social_media == 'YOUTUBE'"
          /></a>
        </div>
      </div>
      <div class="newsfooter">
        <div class="fila1newsfo">
          <form @submit.prevent="suscribirse(email)">
            <h5 class="titnewslfo">SUSCRÍBETE A NUESTRO NEWSLETTER</h5>
            <div class="bloquenewsletter">
              <input
                type="email"
                name=""
                id=""
                placeholder="Correo electrónico"
                v-model="email"
              />
              <button type="submit" class="submitnewsl-btn">Enviar</button>
            </div>
            <div v-if="this.status == 'success'">
              <p class="cart_msg cart_success">{{ this.message }}</p>
            </div>
            <div v-if="this.status == 'error'">
              <p class="cart_msg cart_error">{{ this.message }}</p>
            </div>
          </form>
        </div>
        <img src="../assets/qrsoma.svg" alt="qr" class="qr">
        <div class="fila2newsfo">
          <div class="col1nefo">
            <a href="/politicas"><p>Politicas de Privacidad</p></a>
            <a href="/terminos"><p>Terminos de Uso</p></a>
          </div>
          <div class="col2nefo">
            <img src="../assets/footer/logofooterlit.svg" alt="" />
          </div>
        </div>
      </div>
    </div>
    <div class="fila2footer">
      <p>
        <span>Copyright {{ yyyy }}</span> © Todos los Derechos Reservados.
      </p>
    </div>
  </div>
</template>
<script>
import dayjs from "dayjs";
import { mapActions } from "vuex";
export default {
  data() {
    return {
      email: "",
      status: "",
      message: "",
      yyyy: "2022",
    };
  },
  created() {
    this.yyyy = dayjs().format("YYYY");
    this.getAllInfoPho("phone");
    this.getAllInfoSM("social_media");
    this.getAllInfoHor("horario");
    this.getAllInfoAdr("address");
  },
  computed: {
    phone() {
      return this.$store.getters["phone/data"];
    },
    social_media() {
      return this.$store.getters["social_media/data"];
    },
    horario() {
      return this.$store.getters["horario/data"];
    },
    address() {
      return this.$store.getters["address/data"];
    },
  },
  methods: {
    ...mapActions("phone", ["getAllInfoPho"]),
    ...mapActions("social_media", ["getAllInfoSM"]),
    ...mapActions("horario", ["getAllInfoHor"]),
    ...mapActions("address", ["getAllInfoAdr"]),
    splitday(day){
      let d = day.split('');
      return d[0]+d[1]+d[2]
    },
    suscribirse: async function (email) {
      this.status = "";
      this.message = "";
      let sub_date = dayjs().format("YYYY-MM-DD");
      let data = {
        email,
        sub_date,
      };

      let result = await this.$store.dispatch("suscripciones/addItemSbs", {
        option: "suscripciones",
        item: data,
      });

      if (result.status == "error") {
        this.status = "error";
        this.message = result.message;
        this.delStatus();
      } else {
        // success
        this.status = "success";
        this.message = "Suscripción exitosa!";
        this.email = "";
        this.delStatus();
      }
    },
    delStatus: function () {
      setTimeout(() => this.delMsgs(), 3000);
    },
    delMsgs: function () {
      this.status = "";
      this.message = "";
    },
  },
};
</script>
<style scoped>
/* FOOOOTER */
.bloquefooter {
  background: #191919;
  padding-top: 13.285024154589372vw;
}

.fila1footer h5 {
  font-family: "Montserrat";
  text-align: center;
  color: rgba(228, 4, 36, 1);
  font-size: 5.314009661835748vw;
  line-height: 7.367vw;
  font-weight: 600;
  text-align: center;
}
.colmenu {
  text-align: center;
}
.colmenu ul {
  margin: 0;
  margin-block-start: 0 !important;
  margin-block-end: 0 !important;
  padding-inline-start: 0 !important;
}
.colmenu li {
  font-family: "Montserrat";
  font-size: var(--fs-txtmenufomv);
  color: white;
  text-align: center;
  list-style: none;
  line-height: 13.553140096618357vw;
  transition: 0.5s;
}
.colmenu li:hover {
  color: rgba(228, 4, 36, 1);
}
.bloqueiff a p,
.col1nefo a p {
  transition: 0.5s;
}
.bloqueiff a p:hover,
.col1nefo a p:hover {
  color: rgba(228, 4, 36, 1);
}
.imgfoopc {
  display: none;
}
.colmenu img {
  margin-top: 5vw;
  width: 81.88405797101449vw;
  height: 55.55555555555556vw;
  margin-bottom: 13.768115942028986vw;
}
.bloqueiff {
  text-align: center;
}
.bloqueiff p {
  font-family: "Montserrat";
  font-size: var(--fs-pinfofomv);
  margin: auto;
  line-height: 5.36231884057971vw;
  font-weight: 300;
}
.titpif {
  color: rgba(228, 4, 36, 1);
  font-weight: 500 !important;
}
.txtpif {
  width: 35.02415458937198vw;
  margin: auto;
  color: white;
  font-size: 4.830917874396135vw;
}
.ultpif {
  margin-bottom: 7.488vw !important;
}
.ultpif.last {
  margin-bottom: 17.874vw !important;
}
.redesfooter {
  text-align: center;
  padding-top: 11.83574879227053vw;
}
.redesfooter img {
  width: 15.268115942028986vw;
  height: 14.842995169082126vw;
  filter: var(--sm-icon-color);
}
.btnigfo {
  margin-left: 5vw;
}
.infofooter {
  width: 86%;
  padding-bottom: 20.596618357487923vw;
  border-bottom: 1px solid white;
  margin: auto;
}
.newsfooter {
  width: 85%;
  margin: auto;
  padding-top: 11.83574879227053vw;
}
.fila1newsfo {
  padding-bottom: 18.357vw;
  border-bottom: 1px solid white;
}
.titnewslfo {
  font-family: var(--font-titulo2) !important;
  font-size: 7.314009661835748vw;
  text-transform: uppercase;
  text-align: left !important;
  margin: 0;
  margin-bottom: 8.696vw;
}
.bloquenewsletter {
  height: 13.906763vw;
  display: flex;
  align-items: center;
  overflow: hidden;
}
.newsfooter input {
  width: 53.14009661835749vw;
  font-size: 4.348vw;
  height: 13.2vw;
  background: transparent;
  border: 0.362vw solid #ffffff;
  border-right: 0;
  border-top-left-radius: 4.246376811594203vw;
  border-bottom-left-radius: 4.246376811594203vw;
  border-top-right-radius: 0;
  border-bottom-right-radius: 0;
  text-indent: 13%;
  color: #ffffff !important;
  font-family: "Montserrat";
  font-weight: 300;
  padding: 0;
  -webkit-appearance: none;
}
.newsfooter input::placeholder {
  color: #ffffff;
  opacity: 0.75;
  font-family: var(--font-titulo2);
  font-weight: 300;
  font-style: italic;
}
.newsfooter button {
  background: rgba(228, 4, 36, 1);
  font-family: var(--font-titulo2);
  font-weight: 700;
  height: 13.2vw;
  border: 0.362vw solid rgba(228, 4, 36, 1);
  width: 28.743961352657006vw;
  font-size: 4.348vw;
  color: #ffffff;
  cursor: pointer;
  transition: 0.5s;
  border-top-right-radius: 4.246376811594203vw;
  border-bottom-right-radius: 4.246376811594203vw;
  padding: 0;
}
.newsfooter button:hover {
  background: rgba(228, 4, 36, 1);
  border: 0.362vw solid rgba(228, 4, 36, 1);
}
.fila2newsfo {
  display: flex;
  flex-direction: column-reverse;
}
.col2nefo {
  text-align: center;
  padding-top: 8.937198067632849vw;
  padding-bottom: 10.145vw;
}
.col2nefo img {
  width: 50.02415458937198vw;
  height: auto;
}
.col1nefo {
  text-align: center;
  display: block;
}
.col1nefo a {
  width: 100%;
  color: rgba(68, 233, 200, 1);
  font-family: "Montserrat";
  font-size: var(--fs-pinfofomv);
}
.col1nefo a p {
  margin: 0;
  margin-top: 3.5816425120772946vw;
}
.fila2footer {
  margin: auto;
  width: 85%;
  padding-bottom: 19.565vw;
}
.fila2footer p {
  color: white;
  font-family: "Montserrat";
  font-size: 3.140096618357488vw;
  text-align: center;
  margin: 0;
  margin-top: 6.763vw;
}
.cart_msg {
  position: relative;
  top: 2vw;
}

.hor {
  font-family: "Montserrat";
  font-size: var(--fs-pinfofomv);
  margin: auto;
  line-height: 5.36231884057971vw;
  font-weight: 300;
  color: white;
  margin-bottom: 7.488vw;
}
@media (max-width: 1024px) {
  .menufooter h5 {
    display: none;
  }
  .infofooter h5 {
    font-size: 5.314vw;
  }
.qr {
    margin-top: 7.729vw;
    margin-left: auto;
    margin-right: auto;
    width: 43.237vw;
    display: flex;
}
}
@media (min-width: 1024px) {
  img.qr {
    margin-top: 2.188vw;
    width: 5.313vw;
}
  .col2nefo {
    padding-bottom: 0;
  }
  .titpif {
    color: rgba(228, 4, 36, 1);
    font-weight: 700 !important;
  }
  .bloquefooter {
    padding-top: 3.802083333333333vw;
  }
  .fila1footer {
    display: flex;
    width: 85%;
    border-bottom: 0px solid rgba(228, 4, 36, 1);
    margin: auto;
    padding-left: 8.854166666666668vw;
    height: 20.260416666666668vw;
  }
  .colmenu {
    width: 27%;
    display: flex;
    border-right: 1px solid #ffffff;
    padding-top: 0.8854166666666666vw;
  }
  .menufooter h5 {
    margin-bottom: 1.7187500000000002vw !important;
  }
  .infofooter {
    width: 22%;
    border-right: 1px solid #ffffff;
    margin: 0;
    padding-left: 4.270833333333333vw;
    padding-top: 0.8854166666666666vw;
    padding-bottom: 0vw;
    border-bottom: 0px solid rgba(228, 4, 36, 1);
  }
  .newsfooter {
    width: 40%;
    padding-top: 0.8854166666666666vw;
    margin: 0 !important;
    padding-left: 4.270833333333333vw;
  }
  .fila1footer h5 {
    text-align: left !important;
    font-size: 0.938vw;
    line-height: 1vw;
    font-weight: 600;
    margin: 0;
  }
  .colmenu li {
    font-size: 0.7291666666666666vw;
    text-align: left;
    list-style: circle !important;
    line-height: 2.0458333333333334vw;
    margin-left: 1.25vw;
  }
  .imgfoomv {
    display: none;
  }
  .imgfoopc {
    display: block;
    width: 81.88405797101449vw;
  }
  .colmenu img {
    margin-top: -1vw;
    width: 11.354166666666666vw;
    height: 17.03125vw;
    margin-bottom: 3.768115942028986vw;
    margin-left: 2vw;
  }
  .bloqueiff p {
    /*width: 7.041666666666667vw;*/
    width: 12.041667vw;
    font-size: 0.8333333333333334vw;
    line-height: 1.1250000000000002vw;
    text-align: left;
    font-family: "Montserrat";
    margin: 0;
  }
  .ultpif {
    margin-bottom: 1.3541666666666667vw !important;
  }
  .ultpif.last {
    margin-bottom: 0 !important;
  }
  .redesfooter {
    padding-top: 2.34375vw;
    display: flex;
  }
  .redesfooter img {
    width: 1.875vw;
    height: 1.875vw;
  }
  .btnigfo {
    margin-left: 1vw;
  }
  .infofooter h5 {
    margin-bottom: 1.25vw !important;
  }
  .titnewslfo {
    /*font-family: var(--font-titulo2) !important;*/
    font-weight: 800;
    margin-bottom: 1.0416666666666665vw !important;
  }
  .bloquenewsletter {
    /*height: 2.604166666666667vw;*/
    height: 2.8804166666666666vw;
    display: flex;
    align-items: center;
  }
  .newsfooter input {
    width: 54%;
    height: 2.604166666666667vw;
    border-top-left-radius: 7.246376811594203vw;
    border-bottom-left-radius: 7.246376811594203vw;
    text-indent: 5%;
    color: #ffffff !important;
    font-size: 0.729vw;
    border: 0.162vw solid #ffffff;
    border-right: none;
  }
  .newsfooter button {
    height: 3vw;
    width: 17%;
    font-size: 0.781vw;
    color: #ffffff;
    border-top-right-radius: 7.246376811594203vw;
    border: 0.162vw solid rgba(228, 4, 36, 1);
    border-bottom-right-radius: 7.246376811594203vw;
  }
  .fila1newsfo {
    padding-bottom: 0vw;
    border-bottom: 0px solid rgba(228, 4, 36, 1);
  }
  .fila2newsfo {
    display: flex;
    flex-direction: row;
    /*padding-top: 9.5vw;*/
    padding-top: 1.979vw;
    width: 73%;
  }
  .col1nefo {
    width: 50%;
  }
  .col2nefo {
    width: 50%;
    padding-top: 0vw;
  }
  .col1nefo a {
    width: 30%;
    font-size: var(--fs-txtinfofo);
    text-align: left;
  }
  .col1nefo a p {
    margin: 0;
    font-size: 0.6770833333333334vw;
    margin-top: 0.3125vw;
    font-weight: 300;
  }
  .col2nefo img {
    width: 10.052083333333334vw;
    height: 4.375vw;
    margin-top: -0.5vw;
  }
  .fila2footer {
    padding-bottom: 2.3958333333333335vw;
    border-top: 1px solid #ffffff;
    margin-top: 2vw;
    width: 92%;
  }
  .fila2footer p {
    font-size: 0.6770833333333334vw;
    text-align: center;
    margin: 0;
    margin-top: 1.5625vw;
    width: 92%;
  }

  .txtpif {
    margin: 0;
  }

  .hor {
    font-family: "Montserrat";
    font-size: var(--fs-pinfofomv);
    margin: auto;
    line-height: 5.36231884057971vw;
    font-weight: 300;
    color: white;
    margin-bottom: 2.34375vw;
  }

}
</style>
