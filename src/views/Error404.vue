 <template >
  <div>
    <Navigator/>
    <div class="error-404">
       <div class="content_err">
        <div class="divimg">
          <img class="img_err" src="../assets/error/error.png" alt="">
        </div>
        <div class="errinfo">
            <h2>Algo salio mal...</h2>
            <p>No hemos logrado encontrar el contenido que buscas.  </p>
            <p> Utiliza el siguiente enlace para encontrar  <span>el camino de regreso.</span></p>
        </div>
       </div>
  </div>
  <Footer/>
  </div>

</template>
<script>

import Navigator from '../components/fixed/Navigator.vue'
import Footer from '../components/Footer.vue';
export default {
  name: "Error404",
  data() {
    return {
      status: "error",
      message: "",
    };
  },
  components: {
    Navigator,
    Footer
  },
};
</script>
<style scoped>
.error-404 {
  background-image: url(../assets/errpc.png);
  background-size: 100%; 
  width: 100%;
  height: 100vh;
  display: flex;
  margin-bottom: 1vw;
  justify-content: center;
}
.content_err{
  display: flex;
  margin-top: 11vw;
}
.content_err h2{
  color: rgba(228, 4, 36, 1);
  font-family: 'Montserrat';
  font-weight: 900;
  font-size: 3.802vw;
  margin-top: 10vw;
  margin-bottom: 4.583vw;
}
.content_err p{
  color: rgba(54, 54, 54, 1);
  font-family: 'Montserrat';
  font-weight: 600;
  font-size: 1.042vw;
  line-height: 1.203vw;
  text-align: center;
}
.content_err p span{
  color: rgba(68, 233, 200, 1);
  
}
img.img_err{
  width: 39.948vw;
}
.errinfo{
  width: 34.115vw;
  margin-left: 9.063vw;
}
@media (max-width: 768px) {
.error-404 {
  background-image: url(../assets/errmo.png);
  background-size: 100%; 
    margin-bottom: 9vw;
  }
 .content_err{
  display: flex;
    flex-direction: column-reverse;
  

 }
 .content_err{
  margin-top: 47vw;
 }

 img.img_err{
  width: 75.845vw;
 }

 .content_err h2{
 font-size: 8.454vw;
 font-weight: 700;
 text-align: right;
 margin-top: 0vw;
}
.content_err p{
  font-size: 4.831vw;
  font-weight: 600;
  line-height: 5.580vw;
}
.errinfo{
  width: 82.850vw;
  margin-left: 0vw;
  position: relative;
}
.divimg{
  display: flex;
  justify-content: center;
}
}
@media (min-width: 768px) {

}
</style>