<template>
  <div class="app-container">
    <h1>Llibreta de Contactes</h1>
    <FormulariContacte @afegir-contacte="afegirContacte" />
    <input v-model="cercaNom" placeholder="Cerca per nom" class="search-input" />
    <LlistaContactes :contactes="contactesFiltrats" />
  </div>
</template>

<script setup>
import { ref, computed } from 'vue';
import FormulariContacte from './components/FormulariContactes.vue';
import LlistaContactes from './components/LlistaContactes.vue';

// Llista reactiva de contactes i el terme de cerca
const contactes = ref([]);
const cercaNom = ref('');

// Funció per filtrar contactes basat en el terme de cerca
const contactesFiltrats = computed(() =>
  contactes.value.filter(contacte =>
    contacte.nom.toLowerCase().includes(cercaNom.value.toLowerCase())
  )
);

// Afegeix un nou contacte a la llista
const afegirContacte = contacte => {
  contactes.value.push(contacte);
};
</script>

<style scoped>
.app-container {
  max-width: 600px;
  margin: 0 auto;
  padding: 20px;
  text-align: center;
}
.search-input {
  width: 100%;
  padding: 10px;
  margin: 20px 0;
  font-size: 16px;
}
</style>