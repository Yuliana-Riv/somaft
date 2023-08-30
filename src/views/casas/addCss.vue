<template>
  <div id="AddCss">
    <div class="form-content">
      <form
        @submit.prevent="
          submit(
            id_colaborador,
            titulo,
            estatus,
            renta,
            tipo,
            descripcion,
            ubicacion,
            precio,
            superficie,
            iframe,
            detalles,
            etiquetas,
            act_precio,
            leyenda,
            files,
            cuartos,
            banos,
            cochera,
            superficie_casa
          )
        "
      >
        <div class="grup-form dflx">
          <div class="boxform">
            <label for="titulo" class="titulo">Título </label>
            <input
              v-model="titulo"
              type="text"
              id="titulo"
              name="titulo"
              class="wd-lrg"
              required
            />
          </div>
        </div>

        <!-- <div class="grup-form dflx">
        
        <div class="boxform">
          <label for="descripcion" class="descripcion">Descripción</label>
          <textarea
            v-model="descripcion"
            class="format_ta"
            id="descripcion"
            name="descripcion"
          />
        </div>
     
        
      </div> -->
        <div class="grup-form dflx">
          <div class="boxform">
            <label for="colaborador" class="colaborador">Colaborador</label>
            <input
              v-model="colaborador"
              type="text"
              id="colaborador"
              name="colaborador"
              required
              disabled
            />

            <div>
              <div class="bdy_tbl">
                <div v-for="(item, index) in colaboradores" :key="index">
                  <p
                    :class="{ active_item: id_colaborador == item.id }"
                    @click="
                      (id_colaborador = item.id),
                        (colaborador = item.name + ' ' + item.lastname)
                    "
                  >
                    {{ item.name }} {{ item.lastname }}
                  </p>
                </div>
              </div>
            </div>

            <input
              v-model="search_value"
              type="text"
              :placeholder="'Buscar'"
              class="inp_buscar"
            />
          </div>
          <div class="boxform">
            <label for="colaborador" class="colaborador">Etiquetas</label>

            <div>
              <div class="bdy_tbl">
                <div v-for="(item, index) in etiquetas" :key="index">
                  <p @click="delEtiqueta(index)">{{ item }}</p>
                </div>
              </div>
            </div>

            <input
              v-model="etiqueta"
              type="text"
              :placeholder="'etiqueta'"
              class="inp_buscar"
            />
            <div class="box_rh">
              <p
                :class="{ active_option: etiqueta }"
                @click="addEtiqueta(etiqueta)"
                class="option_btn2"
              >
                Añadir
              </p>
            </div>
          </div>
        </div>

        <div class="grup-form dflx">
          <div class="boxform">
            <label>Activar precio</label>
            <div class="options_btn">
              <p
                @click="act_precio == 'ACTIVO'"
                class="option_btn"
                :class="{ active_option: act_precio == 'ACTIVO' }"
              >
                ACTIVAR
              </p>
              <p
                @click="act_precio = 'INACTIVO'"
                class="option_btn"
                :class="{ active_option: act_precio == 'INACTIVO' }"
              >
                DESACTIVAR
              </p>
            </div>
          </div>
          <div class="boxform" v-if="act_precio == 'ACTIVO'">
            <label for="precio" class="precio">Precio </label>
            <input
              v-model="precio"
              type="number"
              id="precio"
              name="precio"
              min="0"
              step="any"
            />
          </div>
          <div class="boxform" v-if="act_precio == 'INACTIVO'">
            <label for="ubicacion" class="ubicacion">Leyenda </label>
            <input
              v-model="leyenda"
              type="text"
              id="ubicacion"
              name="ubicacion"
            />
          </div>
        </div>

        <div class="grup-form dflx">
          <div class="boxform">
            <label for="ubicacion" class="ubicacion">Zona </label>
            <input
              v-model="ubicacion"
              type="text"
              id="ubicacion"
              name="ubicacion"
            />
          </div>
        </div>
        <div class="grup-form dflx">
          <div class="boxform">
            <label for="superficie" class="superficie"
              >Superficie terreno</label
            >
            <input
              v-model="superficie"
              type="text"
              id="superficie"
              name="superficie"
            />
          </div>
          <div class="boxform">
            <label for="superficie_casa" class="superficie_casa"
              >Superficie construcción</label
            >
            <input
              v-model="superficie_casa"
              type="text"
              id="superficie_casa"
              name="superficie_casa"
            />
          </div>
        </div>
        <div class="grup-form dflx">
          <div class="boxform">
            <label for="cuartos" class="cuartos">Habitaciones </label>
            <input
              v-model="cuartos"
              type="number"
              id="cuartos"
              name="cuartos"
              min="0"
              step="any"
              required
            />
          </div>
          <div class="boxform">
            <label for="banos" class="banos">Baños </label>
            <input
              v-model="banos"
              type="number"
              id="banos"
              name="banos"
              min="0"
              step="any"
              required
            />
          </div>
          <div class="boxform">
            <label for="cochera" class="cochera">Cochera</label>
            <input
              v-model="cochera"
              type="number"
              id="cochera"
              name="cochera"
              min="0"
              step="any"
              required
            />
          </div>
        </div>
        <!-- <div class="grup-form dflx">
          <div class="boxform">
            <label for="iframe" class="iframe">Mapa iframe (opcional) </label>
            <input
              v-model="iframe"
              type="text"
              id="iframe"
              name="iframe"
              class="wd-lrg"
            />
          </div>
         
          
        </div> -->

        <div class="grup-form dflx">
          <div class="boxform">
            <label>Estatus</label>
            <div class="options_btn">
              <p
                @click="estatus = 'ACTIVO'"
                class="option_btn"
                :class="{ active_option: estatus == 'ACTIVO' }"
              >
                VISIBLE
              </p>
              <p
                @click="estatus = 'INACTIVO'"
                class="option_btn"
                :class="{ active_option: estatus == 'INACTIVO' }"
              >
                OCULTO
              </p>
            </div>
          </div>
          <div class="boxform">
            <label>Tipo</label>
            <div class="options_btn">
              <p
                @click="tipo = 'venta'"
                class="option_btn"
                :class="{ active_option: tipo == 'venta' }"
              >
                VENTA
              </p>
              <p
                @click="tipo = 'renta'"
                class="option_btn"
                :class="{ active_option: tipo == 'renta' }"
              >
                RENTA
              </p>
            </div>
          </div>
          <div class="boxform" v-if="tipo == 'venta'">
            <label>Opción a rentar</label>
            <div class="options_btn">
              <p
                @click="renta = 'si'"
                class="option_btn"
                :class="{ active_option: renta == 'si' }"
              >
                SI
              </p>
              <p
                @click="renta = 'no'"
                class="option_btn"
                :class="{ active_option: renta == 'no' }"
              >
                NO
              </p>
            </div>
          </div>
        </div>

        <vue-editor
          id="editor"
          class="quill-editor"
          :editorToolbar="toolbar()"
          v-model="detalles"
        >
        </vue-editor>

        <div class="boxform">
          <label>Imagen/Video</label>
          <div class="options_btn">
            <p
              @click="tipov = 'imagen'"
              class="option_btn"
              :class="{ active_option: tipov == 'imagen' }"
            >
              IMAGEN
            </p>
            <p
              @click="tipov = 'video'"
              class="option_btn"
              :class="{ active_option: tipov == 'video' }"
            >
              VIDEO
            </p>
          </div>
        </div>

        <section v-if="tipov == 'imagen'">
          <div class="form-img">
            <div class="grup-form dflx">
              <div class="boxform">
                <label>Fotos</label>
                <div class="dflx">
                  <label class="filelabel" for="uploadimg">
                    <span>Seleccionar Archivo</span></label
                  >
                </div>

                <input
                  @change="previewFiles"
                  type="file"
                  id="uploadimg"
                  name="uploadimg"
                  class="fileinput"
                  ref="myFiles"
                  multiple
                />
              </div>
            </div>
          </div>
          <div class="grup-form dflx">
            <div class="boxform">
              <div class="bdy_tbl wd-md">
                <div v-for="(img, key) in files" :key="key">
                  <p>{{ img.name }}</p>
                </div>
              </div>
            </div>
          </div>
        </section>
        <section v-if="tipov == 'video'">
          <vue-editor
            id="editor"
            class="quill-editor"
            :editorToolbar="toolbarvideo()"
            v-model="video_link"
          >
          </vue-editor>
        </section>

        <div v-if="status != ''" class="status_messages">
          <div v-if="status == 'success'" class="msg msg_success">
            <p>{{ message }}</p>
          </div>
          <div v-if="status == 'error'" class="msg msg_error">
            <p>{{ message }}</p>
          </div>
        </div>

        <div class="dflx">
          <p @click="wait()" class="btnRegresar">Regresar</p>
          <button class="alta" type="submit">Guardar</button>
        </div>
      </form>

      <div v-if="viewModal" class="modal_view">
        <div id="modal_add">
          <div class="body dflx">
            <h3>Casa agregada</h3>
            <img src="../../assets/default/add.png" alt="icono alerta" />
          </div>

          <div class="modal_add_btns dflx">
            <p @click="Add()" class="otro">Aceptar</p>
            <p @click="toEdit()" class="editar">Editar</p>
            <p @click="back()" class="inicio">Inicio</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import { mapActions } from "vuex";
import { VueEditor } from "vue2-editor";
export default {
  name: "AddCss",
  components: {
    VueEditor,
  },
  data() {
    return {
      status: "",
      message: "",
      id_colaborador: "",
      colaborador: "",
      titulo: "",
      estatus: "ACTIVO",
      renta: "no",
      tipo: "venta",
      cuartos: "",
      banos: "",
      cochera: "",
      superficie_casa: "",
      descripcion: "",
      ubicacion: "",
      precio: 0,
      superficie: "",
      iframe: "",
      detalles: "",
      etiquetas: [],
      etiqueta: "",
      act_precio: "ACTIVO",
      leyenda: "",
      tipov: "imagen",
      video_link: "",
      //MODAL
      files: [],
      viewModal: false,

      search_value: "",
    };
  },
  async created() {
    await this.getAllInfoClb("colaborador");
  },
  computed: {
    colaboradores() {
      let data = this.$store.getters["colaborador/data"];

      if (!Array.isArray(data)) return [];
      if (this.identity.role == "colaborador")
        data = data.filter((item) => item.id == this.identity.sub);

      if (this.search_value != "") {
        let filt = data.filter((item) => {
          const fullname = item.name + " " + item.lastname;
          return this.includesItem(this.search_value, fullname);
        });
        data = filt;
      }

      return data;
    },
    identity() {
      return this.$store.getters["admin/getIdentity"];
    },
  },
  methods: {
    ...mapActions("casas", ["setAddedCss"]),
    ...mapActions("casas", ["setHistoryOptionCss"]),
    ...mapActions("colaborador", ["getAllInfoClb"]),
    ...mapActions("casas", ["getInfoByIdCss"]),
    previewFiles() {
      this.files = this.$refs.myFiles.files;
    },
    addEtiqueta(value) {
      if (value) {
        let newarr = [];
        for (const item of this.etiquetas) {
          newarr.push(item);
        }
        newarr.push(value);
        this.etiquetas = newarr;
        this.etiqueta = "";
      }
    },
    delEtiqueta(index) {
      let newarr = [];
      for (var i = 0; i < this.etiquetas.length; i++) {
        if (i != index) newarr.push(this.etiquetas[i]);
      }
      this.etiquetas = newarr;
    },
    wait: function () {
      setTimeout(() => this.$router.go(), 200);
    },
    includesItem(search, name) {
      name = name.normalize("NFD").replace(/[\u0300-\u036f]/g, "");
      if (search == "") {
        return true;
      }
      name = name.toLowerCase();
      search = search.toLowerCase();
      if (search == "") {
        return false;
      }
      return name.includes(search);
    },
    submit: async function (
      id_colaborador,
      titulo,
      estatus,
      renta,
      tipo,
      descripcion,
      ubicacion,
      precio,
      superficie,
      iframe,
      detalles,
      etiquetas,
      act_precio,
      leyenda,
      files,
      cuartos,
      banos,
      cochera,
      superficie_casa,
      tipov,
      video_link
    ) {
      this.status = "";
      this.message = "";

      if (tipov == "imagen") {
        if (files.length > 0) {
          let result = await this.$store.dispatch("casas/addItemCss", {
            option: "casas",
            item: {
              id_colaborador,
              titulo,
              estatus,
              renta,
              tipo,
              descripcion,
              ubicacion,
              precio,
              superficie,
              iframe,
              detalles,
              etiquetas,
              act_precio,
              leyenda,
              cuartos,
              banos,
              cochera,
              superficie_casa,
            },
          });

          if (result.status == "error") {
            this.status = "error";
            this.message = result.message;
          } else {
            // success
            const id = result.added.id;

            for (const image of files) {
              //Creamos el formData
              var data = new FormData();
              //Añadimos la imagen seleccionada
              data.append("image", image);
              data.append("video_link", video_link);
              data.append("tipov", tipov);
              data.append("id", id);

              //Añadimos el método PUT dentro del formData
              // Como lo hacíamos desde un formulario simple _(no ajax)_
              data.append("_method", "POST");

              await this.$store.dispatch("casas/addItemCss", {
                option: "casas/foto",
                item: data,
              });
            }

            const newadded = await this.getInfoByIdCss({
              id: result.added.id,
              option: "casas",
            });
            this.files = [];
            this.setAddedCss(newadded);
            this.showModal();
          }
        } else {
          this.status = "error";
          this.message = "No has adjuntado ninguna foto.";
          this.delStatus();
        }
      } else if (tipov == "video") {
        // success
        const id = result.added.id;
        const image = "";
        //Creamos el formData
        /**/ var data = new FormData();
        data.append("image", "");
        data.append("video_link", video_link);
        data.append("tipov", tipov);
        data.append("id", id);
        data.append("_method", "POST");

        await this.$store.dispatch("casas/addItemCss", {
          option: "casas/foto",
          item: data,
        });

        const newadded = await this.getInfoByIdCss({
          id: result.added.id,
          option: "casas",
        });
        this.files = [];
        this.setAddedCss(newadded);
        this.showModal();
      }
    },
    delStatus: function () {
      setTimeout(() => this.delMsgs(), 2000);
    },
    delMsgs: function () {
      this.status = "";
      this.message = "";
    },

    showModal: function () {
      this.viewModal = true;
    },

    Add: function () {
      this.status = "";
      this.message = "";

      this.id_colaborador = "";
      this.titulo = "";
      this.estatus = "";
      this.renta = "no";
      this.tipo = "venta";
      this.descripcion = "";
      this.ubicacion = "";
      this.precio = "";
      this.superficie = "";
      this.iframe = "";
      this.detalles = "";
      this.etiquetas = [];
      this.cuartos = "";
      this.banos = "";
      this.cochera = "";
      this.superficie_casa = "";

      this.viewModal = false;
      this.setAddedCss("");
    },
    toEdit: function () {
      this.setHistoryOptionCss("Edit");
      this.viewModal = false;
    },
    back: function () {
      setTimeout(() => this.$router.go(), 200);
    },

    toolbar: function () {
      return [
        ["bold", "italic", "underline", "strike"], // toggled buttons
        ["blockquote", "code-block"],

        [{ header: 1 }, { header: 2 }], // custom button values
        [{ list: "ordered" }, { list: "bullet" }],
        [{ script: "sub" }, { script: "super" }], // superscript/subscript
        [{ indent: "-1" }, { indent: "+1" }], // outdent/indent
        [{ direction: "rtl" }], // text direction

        [{ size: ["small", false, "large", "huge"] }], // custom dropdown
        [{ header: [1, 2, 3, 4, 5, 6, false] }],
        // [ 'link','image' ,'video' ],          // add's image support
        [{ color: [] }, { background: [] }], // dropdown with defaults from theme
        [{ font: [] }],
        [{ align: [] }],

        ["clean"], // remove formatting button
      ];
    },
    toolbarvideo: function () {
      return [["video"]];
    },
  },
};
</script>
<style scoped>
#AddCss label {
  color: var(--color-2);
  font-weight: 700;
  font-size: 0.7291666666666666vw;
  margin-bottom: 0.3vw;
}

#AddCss input,
#AddCss select {
  height: 2.5vw;
  width: 14.716666666666668vw;
  border: 0.052083vw solid var(--color-2);
  border-radius: 0vw 1.5vw 1.5vw 0vw;
  color: var(--color-3);
  font-size: 0.7291666666666666vw;
  font-weight: 500;
  padding-left: 1.09375vw;
}

#select-role {
  height: 2.5vw;
  width: 13.716667vw;
  border: 0.052083vw solid var(--color-2);
  border-radius: 0vw 1.5vw 1.5vw 0vw;
  color: var(--color-3);
  font-size: 0.7291666666666666vw;
  font-weight: 500;
  padding-left: 1.09375vw;
  display: flex;
  align-items: center;
  background-image: url("../../assets/default/blueflecha.svg");
  background-repeat: no-repeat;
  background-position-y: center;
  background-position-x: 12.6vw;
}
#select-role.rounded {
  border-radius: 0vw 1.5vw 0vw 0vw;
  border-left: 0.052083vw solid var(--color-2);
  border-right: 0.052083vw solid var(--color-2);
  border-top: 0.052083vw solid var(--color-2);
  border-bottom: 0;
}
#select-ch:checked ~ .options-cont {
  display: flex;
  position: absolute;
  padding: 0.573vw 1.25vw;
  flex-direction: column;
  background-color: white;
  width: 12.3vw;
  border-left: 0.052083vw solid var(--color-2);
  border-right: 0.052083vw solid var(--color-2);
  border-top: 0;
  border-bottom: 0.052083vw solid var(--color-2);
}
</style>
