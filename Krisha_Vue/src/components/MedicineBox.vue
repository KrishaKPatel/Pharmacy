<template>
    <div>
      <div class="medicine-grid">
        <!-- Use SingleMedicine component for each medicine -->
        <SingleMedicine v-for="medicine in sortedMedicines" :key="medicine.id" :Medicine="medicine" />
      </div>
    </div>
  </template>
  
  <script>
  // Import the SingleMedicine component
  import SingleMedicine from './SingleMedicine.vue'
  
  export default {
    name: 'MedicineBox',
    components: {
      SingleMedicine
    },
    props: {
      medicines: {
        type: Array,
        required: true
      }
    },
    computed: {
      sortedMedicines() {
        // Sort medicines by stock (low stock first)
        return [...this.medicines].sort((a, b) => a.Stock - b.Stock);
      }
    }
  }
  </script>
  
  <style scoped>
  /* Add any required styles here */
  
  .medicine-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(25vw, 1fr)); /* Responsive grid */
    gap: 2em; /* Space between grid items */
    padding: 1em;
  }
  </style>
  