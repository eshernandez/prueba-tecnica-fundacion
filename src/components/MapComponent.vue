<template>
  <h4 class="pb-3">Hola, para continuar. Por favor selecciona un Pais </h4>
  <AutoCompleteComponent name="Buscador de Paises" urlApi="https://restcountries.com/v3.1/all?fields=name,cca3"
    @emitValue="handleValue" />
  <!-- <pre>{{ pais }}</pre>  -->
  <div v-if="dataPais != null">
    <v-card class="mb-3">
      <v-card-text>
        <span class="headline">1. De la propiedad name traer las propiedades common y official</span>
        <div>
          <span class="pb-4">
            <pre class="text-body-2 font-weight-bold">dataPais[0].name.common</pre>
            <pre class="caption">{{ dataPais[0].name.common }}</pre>
          </span>

          <span>
            <pre class="text-body-2 font-weight-bold">dataPais[0].currencies.official  </pre>
            <pre class="caption">{{ dataPais[0].name.official }}</pre>
          </span>
        </div>
      </v-card-text>
    </v-card>

    <v-card class="mb-3">
      <v-card-text>
        <span class="headline">2. De la propiedad currencies traer la propiedad name</span>
        <div>
          <span>
            <pre class="text-body-2 font-weight-bold">dataPais[0].currencies.name</pre>
            <pre class="caption">{{ dataPais[0].currencies }}</pre>
          </span>

        </div>
      </v-card-text>
    </v-card>

    <v-card class="mb-3">
      <v-card-text>
        <span class="headline">3. La propiedad Region</span>
        <div>
          <span>
            <pre class="text-body-2 font-weight-bold">dataPais[0].region</pre>
            <pre class="caption">{{ dataPais[0].region }}</pre>
          </span>
        </div>
      </v-card-text>
    </v-card>

    <v-card class="mb-3">
      <v-card-text>
        <span class="headline">4. La propiedad capital</span>
        <div>
          <span>
            <pre class="text-body-2 font-weight-bold">dataPais[0].capital</pre>
            <pre class="caption">{{ dataPais[0].capital }}</pre>
          </span>
        </div>
      </v-card-text>
    </v-card>

    <v-card class="mb-3">
      <v-card-text>
        <span class="headline">5. La propiedad area</span>
        <div>
          <span>
            <pre class="text-body-2 font-weight-bold">dataPais[0].area</pre>
            <pre class="caption">{{ dataPais[0].area }}</pre>
          </span>
        </div>
      </v-card-text>
    </v-card>

    <v-card class="mb-3">
      <v-card-text>
        <span class="headline">6. Debe desplegar el mapa que está en la propiedad maps en la propiedad googlemaps
        </span>
        <div>
          <span>
            <pre class="text-body-2 font-weight-bold">dataPais[0].maps</pre>
            
          </span>
          <!-- //todo@santiago:Revisar la documentacion oficial del la api, ya que nos retorna un abreviado que no se 
          //carga en el iframe, para que funcione debe ser el enlace completo. -->
          <div>
          <iframe
            :src="dataPais[0].maps.googleMaps"
            width="600" height="450" style="border:0;" allowfullscreen="" loading="lazy">
          </iframe>
            </div>
            <span class="pt-3">
              <a class="text-body-2 font-weight-bold" target="_blank" :href="dataPais[0].maps.googleMaps">click aca para abrir el maps: </a>
              <a class="text-body-2 font-weight-bold" target="_blank" :href="dataPais[0].maps.googleMaps">{{ dataPais[0].maps.googleMaps }}</a>
            </span>
            <span class="caption">Nota: El mapa no se visualiza en el iframe ya que la api provee un link abreviado, pero si se puede abrir en una nueva pestaña
            </span>

        </div>
      </v-card-text>
    </v-card>
  </div>
</template>

<script setup>
import axios from 'axios';
import { ref, defineProps } from 'vue';
import AutoCompleteComponent from './inputs/AutoCompleteComponent.vue';

const pais = ref(null);
const dataPais = ref(null);


const getListPais = async () => {
  try {
    const response = await axios.get(`https://restcountries.com/v3.1/name/${pais.value}`);
    dataPais.value = response.data;
    console.log(dataPais.value);

  } catch (error) {
    console.error('Error fetching data:', error);
  }
};

const handleValue = (value) => {
  console.log(value);
  pais.value = value;
  getListPais()
};


</script>

<style scoped></style>
