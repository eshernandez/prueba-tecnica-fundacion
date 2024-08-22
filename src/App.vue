<template>
  <v-app>
    <MenuToolBarMain />
    <v-main>
      <v-container>
        <Map />
      </v-container>
    </v-main>

    <v-footer app>
      <span>Desarrollado por Eric Hernandez -  &copy; {{ new Date().getFullYear() }}</span>
    </v-footer>
  </v-app>
</template>

<script setup>
import Map from './components/MapComponent.vue'
import MenuToolBarMain from './components/global/MenuToolBarMain.vue'

</script>
