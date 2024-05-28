<template>
    <div class="wonders-container">
      <h1>Les 7 Nouvelles Merveilles Du Monde</h1>
      <div class="grid">
        <div class="grid-item" v-for="wonder in wonders" :key="wonder.id">
          <h2>{{ wonder.lieu }}</h2>
          <p>{{ wonder.pays }}</p>
          <img :src="wonder.pict" :alt="wonder.lieu" @click="selectWonder(wonder)" />
          <div v-if="selectedWonder && selectedWonder.id === wonder.id" v-html="selectedWonder.desc"></div>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  import axios from 'axios';
  
  export default {
    data() {
      return {
        wonders: [],
        selectedWonder: null
      };
    },
    created() {
      axios.get('https://api.atontour.org/v3/sujets/merveilles/?key=736204')
        .then(response => {
          this.wonders = response.data.records;
        })
        .catch(error => {
          console.error("ERREUR", error);
        });
    },
    methods: {
      selectWonder(wonder) {
        this.selectedWonder = this.selectedWonder === wonder ? null : wonder;
      }
    }
  };
  </script>
  
  <style>
  .wonders-container {
    padding: 20px;
    max-width: 1200px;
    margin: 0 auto;
  }
  
  .grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 20px;
  }
  
  .grid-item {
    border: 1px solid #ddd;
    border-radius: 8px;
    padding: 16px;
    background-color: #FDE49C;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
    cursor: pointer;
    transition: transform 0.2s;
  }
  
  .grid-item:hover {
    transform: scale(1.05);
  }
  
  .grid-item img {
    max-width: 100%;
    height: auto;
    border-radius: 8px;
  }
  
  .grid-item h2 {
    font-size: 1.5em;
    margin: 0.5em 0;
  }
  
  .grid-item p {
    font-size: 1em;
    color: #777;
  }
  
  .grid-item div {
    font-size: 1em;
    color: #333;
  }
  </style>
  