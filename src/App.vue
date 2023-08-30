<template>
  <div id="app">
    <router-view />
  </div>
</template>

<script>
import {mapActions} from 'vuex';
export default {
  name: 'App',
  data(){
    return{
      colores:''
    }
  },

  async created(){
    await this.getAllInfoClr('profile')
  
    this.colores = this.profiles
     this.actualizarColores()
  },
  watch:{
      profiles(){
        
         this.actualizarColores()
        
      }
  },
  computed:{
    profiles() {
        return this.$store.getters["profile/data"];
        },
  },
  methods: {
     ...mapActions('colors', ['getAllInfoClr']),
     ...mapActions('profile', ['getAllInfoPrf']),
     actualizarColores(){
        const arr = this.$store.getters["colors/data"];
   
     
        
         if(Array.isArray(arr)){
           for (var i=0; i<arr.length; i++) {
         
             if(i==0){
                document.documentElement.style.setProperty('--color-1', arr[i].code);
             }else if(i==1){
                document.documentElement.style.setProperty('--color-2', arr[i].code);
             }else if(i==2){
               document.documentElement.style.setProperty('--color-3', arr[i].code);
             }else if(i==3){
                document.documentElement.style.setProperty('--color-4', arr[i].code);
             }else if(i==4){
              document.documentElement.style.setProperty('--color-5', arr[i].code);
             }else if(i==5){
                document.documentElement.style.setProperty('--color-6', arr[i].code);
             }else if(i==6){
                document.documentElement.style.setProperty('--color-7', arr[i].code);
             }
          }
         }
     }
  },
}

</script>



<style>
@import './css/default.css';

  @import url('https://fonts.googleapis.com/css2?family=Mukta:wght@300;400;500;600;700;800&family=Open+Sans:wght@300;400;500;600;700;800&family=Sora:wght@100;200;300;400;500;600;700;800&family=Source+Sans+Pro:wght@300;400;600;700&display=swap');

  @import url('https://fonts.googleapis.com/css2?family=DM+Sans:wght@400;500;700&display=swap');

  @import url('https://fonts.googleapis.com/css2?family=Montserrat:wght@200;300;400;500;600;700;800;900&display=swap');

  @import url('https://fonts.googleapis.com/css2?family=Outfit:wght@100;200;300;400;500;600;700;800;900&display=swap');

  @import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700;800;900&display=swap');
  html{
    scroll-behavior: smooth;
  }

  :root{
    /** No eliminar los 7 colores */
    --color-1: #E21F1D;
    --color-2:  #242424;
    --color-3: #A7A7A7;
    --color-4: #F5F5F5;
    --color-5:  #FFFFFF;
    --color-6:  #D9D9D9;
    --color-7:  #FFFFFF;
    
    --Sans: 'Source Sans Pro', sans-serif;
    --Open_Sans: 'Open Sans', sans-serif;
    --Sora: 'Sora', sans-serif;
    --Mukta: 'Mukta', sans-serif;
    --dmsans:'DM Sans', sans-serif;
    --montserrat:'Montserrat', sans-serif;
    --inter: 'Inter', sans-serif;

    --fs-idseccionpc: 0.625vw;

     /* Tipografias */
  --font-titulo1: "Outfit";
  --font-titulo2: "Outfit" ;
  --font-parrafo: "Outfit" ;
  --font-parrafo2: "Outfit" ;

  }

  a {
    text-decoration: none;
    color: inherit;
}
.algc{
  align-items: center;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  margin: 0vw;   
   overflow: hidden;
}


body {
  margin: 0vw;
}


html{
  scroll-behavior: smooth;
}

input:focus-visible {
  outline: none !important;
}

input,
textarea,
select {
  padding-left: 0.5vw;
  outline: none;
}



.dflx{
  display: flex;
}

.pointer{
  cursor: pointer;
}

.jcsb{
  justify-content: space-between;
}

.box_ctr{
  display: flex;
  justify-content: center;
}
.box_rh{
  display: flex;
  justify-content: right;
}

.box_ctr_alg{
  display: flex;
  justify-content: center;
  align-items: center;
}
.crs_ptr{
  cursor: pointer;
}
@media (min-width: 768px) {
  .services .VueCarousel-navigation-button{ 
    width: 1.771vw;
    height: 1.771vw;
    color: white!important;
    border-radius: 10vw;
    background-color: #E40424!important;
    top: 29%!important;
    font-size: .51vw;
    line-height: .51vw;
    display: flex;
    align-items: center;
    justify-content: center;
  }
  .services .VueCarousel-navigation-prev {
    margin-right: 0!important;
    left: -3.750vw!important; 
  }  
  .services .VueCarousel-navigation-next{
    margin-left: 0!important;
    right: -3.75vw!important;
  }
}
</style>
