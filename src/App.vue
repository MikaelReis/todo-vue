<script>
export default {
  data() {
    return {
      number1: 0,
      number2: 0,
      operation: '+',
    };
  },
  computed: {
    result() {
      const num1 = parseFloat(this.number1);
      const num2 = parseFloat(this.number2);
      switch (this.operation) {
        case '+':
          return num1 + num2;
        case '-':
          return num1 - num2;
        case '*':
          return num1 * num2;
        case '/':
          return num2 !== 0 ? num1 / num2 : 'Erro: Divisão por zero';
        default:
          return 0;
      }
    },
  },
};
</script>

<template>
  <div id="app">
    <h1>Calculadora Aritmética 1</h1>
    <div class="calculator">
      <input type="number" v-model="number1" placeholder="Número 1" />
      <select v-model="operation">
        <option value="+">+</option>
        <option value="-">-</option>
        <option value="*">*</option>
        <option value="/">/</option>
      </select>
      <input type="number" v-model="number2" placeholder="Número 2" />
      <p>Resultado: {{ result }}</p>
    </div>
  </div>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  margin-top: 60px;
}

.calculator {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 10px;
}

input,
select {
  padding: 10px;
  font-size: 16px;
  width: 200px;
}

p {
  font-size: 20px;
  font-weight: bold;
}
</style>






