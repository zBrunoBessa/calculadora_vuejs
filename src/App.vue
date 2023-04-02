<script setup>
  import { reactive } from 'vue';
  const estado = reactive ({
    operacao: 'soma',
    numero1: 0,
    numero2: 0,
  });
  const operacoes = () => {
      const {operacao} = estado;
      switch (operacao){
        case 'soma':
          return parseFloat(estado.numero1) + parseFloat(estado.numero2)
        case 'subtracao':
          return parseFloat(estado.numero1) - parseFloat(estado.numero2);
        case 'divisao':
          return parseFloat(estado.numero1) / parseFloat(estado.numero2);
        case 'multiplicacao':
          return parseFloat(estado.numero1) * parseFloat(estado.numero2);  
      }
  }
</script>

<template>
  <div class="container">
    <h1>Calculadora</h1>
    <div>
    <label>Informe o numero 1:</label>
    <input type="number" required @keyup="evento => estado.numero1 = evento.target.value">
  </div>
  <div>
    <label>Informe o numero 2:</label>
    <input type="number" required @keyup="evento => estado.numero2 = evento.target.value">
  </div>
  <div>
  <label>Operação:</label>
    <select @change="evento => estado.operacao = evento.target.value">
      <option value="soma">+</option>
      <option value="subtracao">-</option>
      <option value="divisao">/</option>
      <option value="multiplicacao">x</option>
    </select>
  </div>
    <span>Resultado : <span class="result">{{operacoes(0)}}</span> </span>
  </div>
</template>

<style scoped>
  .container{
    font-size: 24px;
    display: flex;
    flex-direction: column;
    max-height: 400px;
    background-color: #eee;
    padding: 45px;
    align-items: center;


  }
  h1 {
    margin-bottom: 16px;

  }
  input {
    margin-left: 8px;
    width: 80px;
  }
  select {
    margin-left: 12px;
    width: 90px;

  }
  span {
    margin: 10px;
  }
  .result {
    color: #ff1111;
  }
</style>