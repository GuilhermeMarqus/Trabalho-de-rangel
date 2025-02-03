<template>
    <div class="hello">
      <h1>{{ msg }}</h1>
      <p>
        Crie sua conta no Nosso banco <br>
        e <br>
        Deposite sua primeira renda acima de 100 reais
      </p>
  
    </div>
  </template>
  
  <script>
  export default {
    name: 'HelloWorld',
    props: {
      msg: String
    }
  }
  </script>
  
  <!-- Add "scoped" attribute to limit CSS to this component only -->
  <style scoped>
  p {
    color: #2c3e50;
    text-transform: uppercase;
  }
  </style>
  