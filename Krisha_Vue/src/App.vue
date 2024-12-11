<template>
  <div id="app">
    <MyHeader :yourName="'Krisha Patel'" />
    <MedicineBox :medicines="medicines" />
  </div>
</template>

<script>
import MyHeader from './components/MyHeader.vue'
import MedicineBox from './components/MedicineBox.vue'

export default {
  name: 'App',
  components: {
    MyHeader,
    MedicineBox
  },
  data() {
    return {
      medicines: [] // Store the fetched medicines here
    }
  },
  created() {
    this.fetchMedicines();
  },
  methods: {
    async fetchMedicines() {
      try {
        const res = await fetch('https://medicine-app-x1ix.onrender.com/api');
        if (!res.ok) {
          throw new Error('Network response was not ok');
        }
        const data = await res.json();
        this.medicines = data; // Store the fetched data in the medicines array
      } catch (error) {
        console.error('There was a problem with the fetch operation:', error);
      }
    }
  }
}
</script>

<style scoped>
/* Add any required styles here */
</style>
