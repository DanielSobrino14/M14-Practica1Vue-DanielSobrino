<template>
    <ul class="llista-contactes">
      <li v-for="contacte in contactes" :key="contacte.telefon" class="contacte-item">
        <span>{{ contacte.nom }}: </span>
        <a :href="`tel:${contacte.telefon}`">{{ contacte.telefon }}</a>
      </li>
    </ul>
  </template>
  
  <script setup>
  const props = defineProps({
    contactes: Array
  });
  </script>
  
  <style scoped>
  .llista-contactes {
    list-style-type: none;
    padding: 0;
  }
  .contacte-item {
    margin: 10px 0;
    font-size: 18px;
  }
  a {
    color: #00c3ff;
    text-decoration: none;
  }
  a:hover {
    text-decoration: underline;
  }
  </style>
  