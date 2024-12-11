<template>
    <div :class="['medicine_card', { 'low-stock': Medicine.Stock <= 25 }]">
      <h2>{{ Medicine.name }}</h2>
      <p><strong>Price:</strong> {{ Medicine.price }}</p>
      <p><strong>Quantity:</strong> {{ Medicine.quantity }}</p>
      <p><strong>Stock:</strong> {{ Medicine.Stock }}</p>
      <p><strong>Expiry Date:</strong> {{ formatExpiryDate(Medicine["Expiry-date"]) }}</p>
      <p><strong>Category:</strong> {{ Medicine.Category }}</p>
    </div>
  </template>
  
  <script>
  export default {
    name: "SingleMedicine",
    props: {
      Medicine: Object
    },
    methods: {
      formatExpiryDate(date) {
        // Create a new Date object and format it to 'YYYY-MM-DD' format
        const formattedDate = new Date(date);
        return formattedDate.toISOString().split('T')[0]; // Extract the date portion (YYYY-MM-DD)
      }
    }
  };
  </script>
  
  <style scoped>
  .medicine_card {
    display: grid;
    grid-template-columns: 1fr;
    padding: 15px;
    box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19);
    margin-bottom: 1em;
    background-color: #ffb89e;
    color: black;
    border-radius: 4px;
  }
  
  .medicine_card.low-stock {
    background-color: #add8e6;
  }
  
  h2 {
    text-align: center;
    font-weight: bold;
    color: white;
    text-decoration: underline;
    margin-bottom: 10px;
  }
  
  p {
    margin: 5px 0;
    font-size: 16px;
  }
  </style>
  