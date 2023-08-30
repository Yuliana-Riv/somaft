<template>
  <div class="services">
    <div id="servicios" class="sectionservicios">
      <!-- Indicador seccion -->
      <div class="idsecc">
        <h5>03.</h5>
        <hr />
        <h5>Servicios</h5>
      </div>
      <h2 class="tl2">Servicios Inmobiliarios</h2>

      <p class="txt2">
        Somos expertos en bienes raíces. Compra, vende o renta con nosotros
      </p>
      <div class="servs-c">
        <div class="fila-br mo">
          <div
            class="serv-item"
            v-for="(item, key) in serviciosmo.slice(0, sslide)"
            :key="key"
          >
            <div class="div-img">
              <img class="img1" :src="item.img_mo" alt="serv" />
            </div>

            <div class="div-txt" v-html="item.titulo"></div>

            <div class="div-btn">
              <button class="btn11">Contáctanos</button>
            </div>
          </div>

          <p
            class="vermas"
            @click="sslide = sslide++ * 3"
            v-if="serviciosmo.length == 6"
          >
            Ver más
          </p>
        </div>
        <div class="fila-br pc">
          <carousel
            :per-page="4"
            :paginationEnabled="false"
            :navigationEnabled="true"
          >
            <slide v-for="(item, key) in servicios" :key="key">
              <div class="serv-item">
                <div class="div-img">
                  <img class="img1pc" :src="item.img_pc" alt="serv" />
                </div>

                <div class="div-txt" v-html="item.titulo"></div>
                <!-- <a href="https://wa.link/gmgcuf" class="btn">
            <div>Contáctanos</div>
          </a>-->
                <a
                  href="https://api.whatsapp.com/send?phone=526621746966&text=%C2%A1Hola!%20Me%20gustar%C3%ADa%20m%C3%A1s%20informaci%C3%B3n%20de%20sus%20servicios%20inmobiliarios"
                  target="_blank"
                  rel="noopener noreferrer"
                >
                  <div class="div-btn">
                    <button class="btn11">Contáctanos</button>
                  </div></a
                >
              </div>
            </slide>
          </carousel>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import { Carousel, Slide } from "vue-carousel";
export default {
  components: {
    Carousel,
    Slide,
  },
  data() {
    return {
      sslide: 3,
      servicios: [
        {
          titulo:
            "<p class='tl'>Compraventa de contado o con Crédito Hipotecario <span class='stl'>(INFONAVIT, FOVISSTE, bancarios)</span><p>",
          telefono: "",
          img_mo: require("../assets/compra_mo.png"),
          img_pc: require("../assets/compra_pc.png"),
        },
        {
          titulo:
            "<p class='tl'>Consulta de créditos de liquidez, estimaciones de valor para venta y avalúos<p>",
          telefono: "",
          img_mo: require("../assets/consulta_mo.png"),
          img_pc: require("../assets/consulta_pc.png"),
        },
        {
          titulo:
            "<p class='tl'>Orientación legal para regularización de bienes inmuebles<p>",
          telefono: "",
          img_mo: require("../assets/orientacion_mo.png"),
          img_pc: require("../assets/orientacion_pc.png"),
        },
        {
          titulo: "<p class='tl'>Cursos de Capacitación con válidez oficial<p>",
          telefono: "",
          img_mo: require("../assets/cursos_mo.png"),
          img_pc: require("../assets/cursos_pc.png"),
        },
        {
          titulo:
            "<p class='tl'>Acompañamiento integral en procesos de transferencia de bienes inmuebles y procesos judiciales inmobiliarios<p>",
          telefono: "",
          img_mo: require("../assets/negocio_mo.png"),
          img_pc: require("../assets/negocio_pc.png"),
        },
        {
          titulo:
            "<p class='tl'>Saneamiento de estatus jurídico de propiedades <span class='stl'>(Protocolización de juicios sucesorios, sentencias de divorcio, cancelación de gravámenes, donaciones, etc.)</span><p>",
          telefono: "",
          img_mo: require("../assets/casa_mo.png"),
          img_pc: require("../assets/casa_pc.png"),
        },
      ],
      serviciosmo: [
        {
          titulo:
            "<p class='tl'>Compraventa de contado o con Crédito Hipotecario <span class='stl'>(INFONAVIT, FOVISSTE, bancarios)</span><p>",
          telefono: "",
          img_mo: require("../assets/compra_mo.png"),
          img_pc: require("../assets/compra_pc.png"),
        },
        {
          titulo:
            "<p class='tl'>Consulta de créditos de liquidez, estimaciones de valor para venta y avalúos<p>",
          telefono: "",
          img_mo: require("../assets/consulta_mo.png"),
          img_pc: require("../assets/consulta_pc.png"),
        },
        {
          titulo:
            "<p class='tl'>Orientación legal para regularización de bienes inmuebles<p>",
          telefono: "",
          img_mo: require("../assets/orientacion_mo.png"),
          img_pc: require("../assets/orientacion_pc.png"),
        },
        {
          titulo: "<p class='tl'>Cursos de Capacitación con válidez oficial<p>",
          telefono: "",
          img_mo: require("../assets/cursos_mo.png"),
          img_pc: require("../assets/cursos_pc.png"),
        },
        {
          titulo:
            "<p class='tl'>Acompañamiento integral en procesos de transferencia de bienes inmuebles y procesos judiciales inmobiliarios<p>",
          telefono: "",
          img_mo: require("../assets/negocio_mo.png"),
          img_pc: require("../assets/negocio_pc.png"),
        },
        {
          titulo:
            "<p class='tl'>Saneamiento de estatus jurídico de propiedades <span class='stl'>(Protocolización de juicios sucesorios, sentencias de divorcio, cancelación de gravámenes, donaciones, etc.)</span><p>",
          telefono: "",
          img_mo: require("../assets/casa_mo.png"),
          img_pc: require("../assets/casa_pc.png"),
        },
      ],
    };
  },
};
</script>
<style scoped>
.services {
  background-image: url(../assets/fondosermo.png);
  background-size: 100%;
  padding-bottom: 14vw;
}
.tl2 {
  font-family: "Montserrat";
  text-align: center;
}

.idsecc {
  display: flex;
  width: 40%;
  margin: auto;
  padding-top: 14.492753623188406vw;
}

.idsecc h5 {
  font-size: 2.657004830917874vw;
  font-family: "Montserrat";
  text-transform: uppercase;
  color: #363636;
  margin: 0;
}

.idsecc hr {
  width: 14.975845410628018vw;
  border: 0.078vw solid gray;
  margin-top: 1vw;
  background: #ffffff;
}

.tl2 {
  color: #e40424;
  font-family: "Montserrat";
  font-weight: 700;
  text-align: center;
  margin-left: 17.32367149758454vw;
  margin-right: 17.32367149758454vw;
  font-size: 8.454106280193237vw;
  line-height: 90.5%;
  margin-top: 27.294685990338163vw;
}

.txt2 {
  color: #575656;
  font-weight: 600;
  text-align: center;
  font-size: 4.3478260869565215vw;
  margin-left: 15.942028985507244vw;
  margin-right: 15.942028985507244vw;
}
.img1 {
  margin-left: 30.676328502415455vw;
  margin-right: 30.676328502415455vw;
}

:deep(.tl) {
  font-family: "Montserrat";
  font-size: 4.3478260869565215vw;
  color: #363636;
  text-align: center;
  font-weight: 700;
  width: 76.81159420289855vw;
  margin: auto;
  margin-bottom: -1vw;
}

:deep(.stl) {
  font-family: "Montserrat";
  font-size: 4.3478260869565215vw;
  text-align: center;
  margin-top: -1vw;
  margin-bottom: 4.3478260869565215vw;
  font-weight: 400;
}

.sectionservicios a.btn {
  width: 100%;
}
.sectionservicios a.btn div {
  border: 0.5vw solid #e40424;
  color: white;
  background-color: #e40424;
  padding: 6.763vw 0;
  text-align: center;
  border-radius: 100vw;
  font-weight: 800;
  font-size: 4.348vw;
  transition: 0.5s;
  width: 80.82125603864734vw;
  margin-top: 4.3478260869565215vw;
  margin-bottom: 10.628019323671497vw;
  margin-left: 9vw;
}
.sectionservicios a.btn div:hover {
  background-color: #e40424;
  color: white;
}
.sectionservicios a.btn.prox {
  pointer-events: none;
}
.sectionservicios a.btn.prox div {
  border: 0.1vw solid #e40424;
  color: #e40424;
  background-color: #e40424;
  font-weight: 500;
}

.vermas {
  color: #e40424;
  font-size: 4.3478260869565215vw;
  font-weight: 900;
  text-align: center;
}
#btns {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
}

#btns > div {
  width: 50%;
}

.img1pc {
  display: none;
}

.sectiondirectorio .servs-c {
  padding-bottom: 30.676vw;
}
.sectiondirectorio .serv-item {
  width: 65.821vw;
  margin: 0 auto 8.696vw;
  display: flex;
  flex-direction: column;
  align-items: center;
}
.sectiondirectorio .servs-c.dir-c {
  width: 91.546vw;
  margin: auto;
}
.sectiondirectorio .dir-c .serv-item {
  width: 91.546vw;
}
.sectiondirectorio .dir-c .serv-item img {
  width: 48.792vw;
}
.sectiondirectorio .dir-c .stl {
  width: 80%;
}

.sectiondirectorio .serv-item img {
  width: 100%;
}
.sectiondirectorio .tl {
  font-family: var(--font-titulo1);
  color: var(--co-t1serv);
  font-weight: 700;
  font-size: 4.831vw;
  line-height: 111%;
  text-align: center;
  margin: 4.348vw 0;
}
.sectiondirectorio .stl {
  font-weight: 300;
  font-size: 3.865vw;
  line-height: 4.831vw;
  color: var(--co-t2serv);
  text-align: center;
  width: 52.899vw;
  margin-bottom: 1.5104166666666667vw;
}

.btn11 {
  border: 0.5vw solid #e40424;
  color: white;
  background-color: #e40424;
  background-image: url(../assets/wha.png);
  background-repeat: no-repeat;
  background-size: 7.005vw 7.005vw;
  background-position-x: 12.278vw;
  background-position-y: 3.865vw;
  padding: 0;
  width: 59.903vw;
  height: 14.492753623188406vw;
  text-align: center;
  border-radius: 100vw;
  font-weight: 700;
  font-family: "Montserrat";
  /*font-size: 4.348vw;*/
  font-size: 4.048vw;
  margin-left: 20.08937198067633vw;
  transition: 0.5s;
  text-align: center;
  margin-top: 2.3478260869565215vw;
  margin-bottom: 10.628019323671497vw;
  text-indent: 12vw;
  cursor: pointer;
}

::placeholder {
  font-family: "Montserrat";
  font-size: 4.830917874396135vw;
  font-style: italic;
  color: #ffffff;
  font-weight: 400;
}
.fila-br.mo {
  display: block;
}
.fila-br.pc {
  display: none;
}
@media (min-width: 768px) {
  .fila-br.mo {
    display: none;
  }
  .fila-br.pc {
    display: block;
  }
  .services {
    padding-bottom: 2.2vw;
    background-image: url(../assets/fondoserpc.png);
  }

  .filanosotros .idsecc {
    display: flex;
    padding-top: 5vw;
    padding-left: 0vw;
  }
  .tl2 {
    font-family: "Montserrat";
    text-align: center;
    font-size: 2.604166666666667vw;
  }

  .tl2 {
    color: #e40424;
    font-family: "Montserrat";
    font-weight: 700;
    text-align: center;
    margin: auto;
    font-size: 8.454106280193237vw;
    line-height: 90.5%;
    margin-top: 5.989583333333334vw;
    font-size: 2.604166666666667vw;
  }

  .txt2 {
    color: #575656;
    font-weight: 600;
    text-align: center;
    font-size: 1.0416666666666665vw;
    margin-top: 1.9791666666666665vw;
    margin-left: 27.083333333333332vw;
    margin-right: 27.083333333333332vw;
  }
  .img1 {
    display: none;
  }

  .img1pc {
    display: block;
    width: 8.229vw;
    height: 7.813vw;
    margin: auto;
  }

  .fila-br {
    width: 56.458333333333336vw;
    margin: auto;
    margin-top: 3.854166666666667vw;
    display: flex;
    justify-content: center;
    margin-bottom: 10.628019323671497vw;
  }
  .fila-br .fbr {
    width: 41.21256038647343vw;
    height: 41.21256038647343vw;
    margin-bottom: 5vw;
    overflow: hidden;
  }

  :deep(.tl) {
    font-family: "Montserrat";
    font-size: 0.8333333333333334vw;
    color: #363636;
    text-align: center;
    font-weight: 700;
    /*width:13vw;*/
    width: 100%;
    padding-left: 0vw;
  }
  :deep(.stl) {
    font-family: "Montserrat";
    font-size: 0.8333333333333334vw;
    text-align: center;
    margin-top: 1vw;
    margin-bottom: 0.3478260869565215vw;
    width: 13vw;
  }

  .sectionservicios a.btn {
    width: 10%;
  }
  .sectionservicios a.btn div {
    border: 0.5vw solid #e40424;
    color: white;
    background-color: #e40424;
    padding: 1.763vw;
    text-align: center;
    border-radius: 100vw;
    font-weight: 800;
    font-size: 0.848vw;
    transition: 0.5s;
    width: 10.104166666666666vw;
    margin-top: 2.3478260869565215vw;
    margin-bottom: 10.628019323671497vw;
    margin-left: 9vw;
  }
  .sectionservicios a.btn div:hover {
    background-color: #e40424;
    color: white;
  }
  .sectionservicios a.btn.prox {
    pointer-events: none;
  }
  .sectionservicios a.btn.prox div {
    border: 0.1vw solid #e40424;
    color: #e40424;
    background-color: #e40424;
    font-weight: 500;
  }

  .vermas {
    color: #e40424;
    font-size: 4.3478260869565215vw;
    font-weight: 900;
    text-align: center;
  }
  .sectiondirectorio .tl {
    font-size: 1.3541666666666667vw;
    font-family: "Montserrat";
    margin-bottom: 1vw;
    margin-bottom: -1vw;
    text-align: center;
  }

  .sectiondirectorio .dir-c .stl {
    width: 20%;
    line-height: 1vw;
  }

  .sectiondirectorio .stl {
    font-size: 0.9895833333333333vw;
    font-family: "Montserrat";
    width: 20%;
  }

  .serv-item {
    width: 11.302vw;
    /*margin: 0 2.057vw;*/
    margin: 0 auto;
  }

  .tl1 {
    margin-top: 0vw;
  }

  .vermas {
    display: none;
  }

  .btn11 {
    border: 0;
    color: white;
    background-image: url(../assets/wha.png);
    background-repeat: no-repeat;
    background-position-x: 1.745vw;
    background-position-y: 0.677vw;
    background-color: #e40424;
    background-size: 1.1541666666666668vw 1.1541666666666668vw;
    /*width: 12.104166666666666vw;*/
    width: 100%;
    height: 2.4479166666666665vw;
    padding: 0vw;
    text-align: center;
    padding-left: 0;
    border-radius: 100vw;
    font-weight: 700;
    font-size: 0.783vw;
    line-height: 0.783vw;
    transition: 0.5s;
    margin-top: 2.3478260869565215vw;
    margin-bottom: 0;
    margin-left: 0vw;
    text-indent: 1.4vw;
  }

  .div-img {
    width: 8.233854166666667vw;
    height: 7.8125vw;
    margin: auto;
  }

  .div-txt {
    /*width: 12.5770833333333327vw;*/
    width: auto;
    min-height: 3.75vw;
    max-height: 5.75vw;
    margin: 0.938vw auto 0;
  }

  .div-btn {
    width: 10.5vw;
    height: 2.4479166666666665;
    margin: auto;
  }

  ::placeholder {
    color: #ffffff;
    font-size: 1.0416666666666665vw;
    font-style: italic;
  }

  .idsecc {
    display: flex;
    width: 13%;
    margin: auto;
    padding-top: 6.5vw;
  }
  .idsecc h5 {
    font-size: 0.625vw;
    margin: 0;
  }
  .idsecc hr {
    width: 3.229166666666667vw;
    background: gray;
    border: 0.078vw solid gray;
    margin-top: 0.35vw;
  }
}
@media (max-width: 767px) {
  .servs-c .tl {
    margin-bottom: 4.348vw;
  }
}
</style>
