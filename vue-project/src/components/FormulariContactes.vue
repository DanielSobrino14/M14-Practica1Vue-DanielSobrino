<template>
    <form @submit.prevent="enviarContacte">
      <input v-model="nom" placeholder="Nom" required />
      <input v-model="telefon" placeholder="Telèfon" required />
      <button type="submit">Afegeix Contacte</button>
    </form>
  </template>
  
  <script setup>
  import { ref } from 'vue';
  
  // Variables reactives per emmagatzemar el nom i el telèfon del contacte
  const nom = ref('');
  const telefon = ref('');
  
  // Definició de l'event per emetre
  const emetre = defineEmits(['afegir-contacte']);
  
  // Enviar el contacte a l'aplicació principal
  const enviarContacte = () => {
    if (nom.value && telefon.value) {
      const nouContacte = {
        nom: nom.value,
        telefon: telefon.value,
      };
      emetre('afegir-contacte', nouContacte);
      nom.value = '';
      telefon.value = '';
    }
  };
  </script>
  
  <style scoped>
  form {
    display: flex;
    flex-direction: column;
    gap: 10px;
    margin-bottom: 20px;
  }
  input {
    padding: 10px;
    font-size: 16px;
  }
  button {
    padding: 10px;
    font-size: 16px;
    background-color: #ff0000;
    color: white;
    border: none;
    cursor: pointer;
  }
  </style>
  