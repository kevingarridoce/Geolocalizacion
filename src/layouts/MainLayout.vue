<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated>
      <q-toolbar>
        

        <q-toolbar-title>
         
         Encontrar ubicacion

      
        </q-toolbar-title>

       
      </q-toolbar>
    </q-header>

    
    <q-page-container>
     
     <GmapMap
      :center="{lat:-0.283994, lng: -78.493783}"
      :zoom="16"
      map-type-id="terrain"
      class="google-map"
      ref="googlemap"
    >
      
    </GmapMap>
    <q-icon class="pin" name="my_location" style="font-size: 3rem;"/>
     <q-btn color="primary" class="ObtenerUbicacion" @click="getLocation">
       Obtener ubicacion
     </q-btn>
    </q-page-container>
  </q-layout>
</template>

<script>
import Vue from 'vue'
import * as VueGoogleMaps from 'vue2-google-maps'



Vue.use(VueGoogleMaps, {
  load: {
    key: 'AIzaSyCqUMBqPxrL9pkmayujzy9Uvlx19Quza2c'
  }
})
import{QLayout,
QToolbar,
QToolbarTitle,
QIcon,
QBtn
} from 'quasar'

export default {
  name: 'MainLayout',
  
  components: {  QLayout, QToolbarTitle, QToolbar,QIcon, QBtn },
  methods:{
    getLocation(){
      navigator.geolocation.getCurrentPosition(
        position => {
          console.log('position:', position)
          this.lat= position.coords.latitude
          this.lon= position.coords.longitude
          this.ubicacionData()
        })
      
    },
    ubicacionData(){
        return this.lat;
    }
  }
 

};
</script>
<style lang="css">
.google-map{
  width: 100vw;
  height: 90vh;

}
.vue-map-hidden{
  display: inherit imp !important;
 
}
.pin{
  position: fixed;
  top:50%;
   width: 100%;
  text-align:center ;
  
}
.ObtenerUbicacion{
  position: absolute;
  bottom: 0;
  left: 0;
width:100%;
z-index: 2;

}

</style>
