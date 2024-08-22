<template>
    <v-app-bar app color="primary" dark>
      <div class="d-flex align-center">
        <v-img
          alt="Vuetify Logo"
          class="shrink mr-2"
          contain
          src="https://cdn.vuetifyjs.com/images/logos/vuetify-logo-dark.png"
          transition="scale-transition"
          width="40"
        />

        <v-title class="text-h6">
          Consulta el mapa
        </v-title>
      </div>

      <v-spacer></v-spacer>

      <v-btn
        href="http://localhost:3000/"
        
        text
      >
        <span class="mr-2">App version 1.0</span>
        <v-icon>mdi-open-in-new</v-icon>
      </v-btn>
    </v-app-bar>

    <v-navigation-drawer app>
      <v-list-item
        v-for="link in links"
        :key="link.text"
        link
      >
        <v-list-item-icon>
          <v-icon>{{ link.icon }}</v-icon>
        </v-list-item-icon>

        <v-list-item-content>
          <v-list-item-title>{{ link.text }}</v-list-item-title>
        </v-list-item-content>
      </v-list-item>
    </v-navigation-drawer>
</template>

<script setup>
const links = [
  { icon: 'mdi-home', text: 'Inicio' },
]
</script>