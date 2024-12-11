<template>
    <div>
      <h1>Welcome to Pharmacy</h1>
      <h4>{{ yourName }}</h4>
    </div>
  </template>
  
  <script>
  export default {
    name: 'MyHeader',
    props: {
      yourName: String // Only passing yourName as a prop
    }
  };
  </script>
  
  <style scoped>
  div {
    text-align: center;
  }
  </style>
  