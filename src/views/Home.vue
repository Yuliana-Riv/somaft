<template >
  <div>
    <Navigator />
    <Propiedades/>
    <SectionBanner1/>    
    <SectionNosotros/>
    <SectionDirectorio/>
    <SectionServicios/>
    <SectionBanner2/>
    <SectionForm/>
    <Footer/>
      
  </div>
</template>
<script>

import {url} from '../global/index'; 
import Navigator from '../components/fixed/Navigator.vue'
import Propiedades from '../components/propiedades.vue';
import SectionBanner1 from '../components/SectionBanner1.vue';
import SectionNosotros from '../components/SectionNosotros.vue';
import SectionDirectorio from '../components/SectionDirectorio.vue';
import SectionServicios from '../components/SectionServicios.vue';
import SectionForm from '../components/SectionForm.vue';
import SectionBanner2 from '../components/SectionBanner2.vue';
import Footer from '../components/Footer.vue';
export default {
  name:'HOME',
  components: {
    Navigator,
    Propiedades,
    SectionBanner1,
    SectionNosotros,
    SectionDirectorio, 
    SectionServicios,
    SectionBanner2,
    SectionForm,
    Footer    

  }   
}
</script>
