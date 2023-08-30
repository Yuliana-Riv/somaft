<template>
    <div id="Dashboard">
         <SideMenu /> 
        <div class="content_sections">
          <Sections :option="'Default'" />
        
        </div>
    </div>
</template>
<script>

import SideMenu from '../../components/SideMenuClb.vue'
import Sections from '../../components/SectionsClb.vue' 


  

export default {
  name: 'dashcolab',
  components:{
    SideMenu,
    Sections
  },
 
}
</script>
<style scoped>
   
   #Dashboard{
     display: flex;
   }

   .content_sections{
     background: var(--color-5);
     min-height: 59.25VW;
     width: 78.17708333333333VW;
     
   }
</style>
