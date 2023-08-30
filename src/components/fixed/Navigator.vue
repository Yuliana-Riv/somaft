<template>
  <div id="Navigator" :class="{ active: act == true, scrolled: scrollP > 0 }">
    <div class="nav-b" :class="{ transparent: $route.name == '404' }">
      <div class="nav-c">
        <div class="sc1" :class="{ transparent: $route.name == '404' }">
          <a href="/" class="logo">
            <img src="../../assets/navigator/soma.svg" alt="logo" />
          </a>
          <img
            src="../../assets/navigator/Bars.svg"
            alt="bars"
            class="bars pointer"
            @click="act = true"
          />
        </div>
        <div
          class="close-b"
          @click="act = false"
          :class="{ active: act == true }"
        >
          <div class="menu-conts" :class="{ active: act == true }" @click.stop>
            <img
              src="../../assets/navigator/close.svg"
              alt="cross"
              class="bars pointer"
              @click="act = false"
            />
            <div class="m-items">
              <a
                href="/"
                :class="{ active: hop == 'buscador' }"
                @click="click('buscador')"
                >BUSCADOR</a
              >
              <a
                href="/#nosotros"
                :class="{ active: hop == 'nosotros' }"
                @click="click('nosotros')"
                >NOSOTROS</a
              >
              <a
                href="/#directorio"
                :class="{ active: hop == 'agentes' }"
                @click="click('agentes')"
                >AGENTES</a
              >
              <a
                href="/#servicios"
                :class="{ active: hop == 'servicios' }"
                @click="click('servicios')"
                >SERVICIOS</a
              >

              <a
                href="/#contacto"
                :class="{ active: hop == 'contacto' }"
                @click="click('contacto')"
                >CONTACTO</a
              >
              <div class="sm-c">
                <a
                  v-for="(sm, i) in social_media"
                  :key="i"
                  :href="sm.link"
                  target="_blank"
                  rel="noopener noreferrer"
                  @click="act = false"
                >
                  <img
                    src="../../assets/navigator/FB.svg"
                    alt=""
                    class="sm-l"
                    v-if="sm.social_media == 'FACEBOOK'"
                  />
                  <img
                    src="../../assets/navigator/IG.svg"
                    alt=""
                    class="sm-l"
                    v-if="sm.social_media == 'INSTAGRAM'"
                  />
                  <img
                    src="../../assets/navigator/TW.svg"
                    alt=""
                    class="sm-l"
                    v-if="sm.social_media == 'TWITTER'"
                  />
                  <img
                    src="../../assets/navigator/TT.svg"
                    alt=""
                    class="sm-l"
                    v-if="sm.social_media == 'TIKTOK'"
                  />
                  <img
                    src="../../assets/navigator/LN.svg"
                    alt=""
                    class="sm-l"
                    v-if="sm.social_media == 'LINKEDIN'"
                  />
                  <img
                    src="../../assets/navigator/YT.svg"
                    alt=""
                    class="sm-l"
                    v-if="sm.social_media == 'YOUTUBE'"
                  />
                  <img
                    src="../../assets/navigator/WA.svg"
                    alt=""
                    class="sm-l"
                    v-if="sm.social_media == 'WHATSAPP'"
                  />
                </a>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import { mapActions } from "vuex";
export default {
  data() {
    return {
      act: false,
      scrollP: localStorage.getItem("scroll"),
    };
  },
  created() {
    let nav = localStorage.getItem("ruta");
    this.setHistoryOptionMain(nav);
    this.getAllInfoSM("social_media");
  },
  computed: {
    hop() {
      return this.$store.getters["main/getHistoryOption"];
    },
    social_media() {
      return this.$store.getters["social_media/data"];
    },
  },
  methods: {
    ...mapActions("main", ["setHistoryOptionMain"]),
    ...mapActions("social_media", ["getAllInfoSM"]),

    click(val) {
      window.localStorage.setItem("ruta", val);
      this.setHistoryOptionMain(val);
      this.act = false;
    },

    scroll(event) {
      let number = event.target.documentElement.scrollTop;
      let offset = number * 1;
      localStorage.setItem("scroll", offset);
      this.scrollP = localStorage.getItem("scroll");
    },
  },
  mounted() {
    window.addEventListener("scroll", this.scroll);
  },
};
</script>
<style>
#Navigator {
  width: 100vw;
  height: 24.367vw;
  z-index: 1000;
  overflow: hidden;
  position: fixed;
  transition: 0.5s;
}
.transparent {
  background-color: transparent !important;
}
#Navigator.active {
  height: 100vh;
}
.nav-b {
  width: 100vw;
  height: fit-content;
}
.nav-c .m-items a {
  font-family: "Montserrat";
  font-style: normal;
  color: rgba(87, 86, 86, 1);
  font-weight: 600;
  text-decoration-color: transparent;
  transition: 0.5s;
}
.nav-c .m-items a:hover {
  color: #e40424;
}
@media (max-width: 768px) {
  .nav-c .close-b {
    height: 100vh;
    width: 100vw;
    position: absolute;
    top: 0;
    left: 0;
    pointer-events: none;
    background: transparent;
    transition: 0.5s;
  }
  .nav-c .close-b.active {
    pointer-events: all;
    background: #0000007a; /**/
  }
  .menu-conts {
    width: 61.836vw;
    height: 100vh;
    position: absolute;
    top: 0;
    right: -100vw;
    transition: 0.5s;
    background: white;
    padding: 10.386vw 7.729vw 11.836vw;
  }
  .menu-conts.active {
    right: 0;
  }
  .nav-c .sc1 {
    display: flex;
    justify-content: space-between;
    align-items: center;
    width: auto;
    padding: 4.589vw 7.971vw;
    background-color: white;
  }
  .nav-c .m-items {
    display: flex;
    flex-direction: column;
    align-items: flex-end;
  }
  .nav-c .sc1 .bars {
    width: 9.662vw;
  }
  .nav-c a.logo img {
    /*width: 50vw;*/
    width: 25.181vw;
  }

  .nav-c .bars {
    margin-left: auto;
    display: flex;
    width: 10.628vw;
  }
  .nav-c .menu-conts .bars {
    margin-bottom: 13.043vw;
  }
  .nav-c .m-items a {
    margin-bottom: 7.488vw;
    font-size: 6.522vw;
    line-height: 9.662vw;
  }
  .nav-c .sm-c {
    width: 25.121vw;
    display: flex;
    justify-content: space-between;
    height: fit-content;
  }
  .nav-c .sm-c a {
    margin-bottom: 0;
  }
  .nav-c .sm-c a .sm-l {
    width: 10.386vw;
    height: 10.386vw;
  }
}

@media (min-width: 768px) {
  .nav-b {
    background-color: white;
  }
  #Navigator {
    height: 10.5vw;
  }
  #Navigator.scrolled{
    height: 5.5vw;
  }
  .nav-c {
    display: flex;
    justify-content: space-between;
    align-items: center;
    height: fit-content;
    padding: 1.281vw 5.104vw;
    transition: 0.5s;
  }
  .scrolled .nav-c {
    padding: 0.81vw 5.104vw;
  }
  .nav-c .bars {
    display: none;
  }
  .nav-c a.logo img {
    width: 13.125vw;
    transition: 0.5s;
  }
  .scrolled .nav-c a.logo img {
    width: 6.125vw;
  }
  .nav-c .m-items {
    display: flex;
    align-items: center;
    height: 3.958vw;
  }
  .nav-c .m-items a {
    margin-right: 1.458vw;
    font-size: 0.677vw;
    line-height: 0.99vw;
    font-weight: 900;
  }
  .nav-c .m-items a.active {
    color: #e40424 !important;
  }
  .nav-c .sm-c {
    display: flex;
    justify-content: space-between;
    /*width: 2.292vw;*/
    width: fit-content;
  }
  .nav-c .sm-c a .sm-l {
    width: 0.938vw;
    height: 0.938vw;
  }
  .nav-c .sm-c a {
    margin-right: 0;
  }
}
</style>
