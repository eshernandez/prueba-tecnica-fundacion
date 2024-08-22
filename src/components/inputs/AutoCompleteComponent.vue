<template>
    <v-autocomplete
        v-model="selectedItem"
        :items="items"
        :label="props.name"
        outlined
        clearable
        dense
        no-data-text="Vacio"
    ></v-autocomplete>
</template>

<script setup>
import { ref, onMounted, defineProps, defineEmits, watch } from 'vue';

const emit = defineEmits(['emitValue'])

const props = defineProps({
    urlApi: {
        type: String,
        required: true
    },
    name: {
        type: String,
        required: true
    }
});

const selectedItem = ref(null);
const items = ref([]);

onMounted(async () => {
    try {
        const response = await fetch(props.urlApi);
        const data = await response.json();
        items.value = data.map(item => item.name.common);
        // console.log(items.value);
        
    } catch (error) {
        console.error(error);
    }
});
watch(selectedItem, (newValue) => {
    emit('emitValue', selectedItem.value);
    console.log(newValue);
});

</script>

<style scoped>
</style>
