<script setup>
import { reactive, computed } from 'vue';
import CalculatorHeader from './components/CalculatorHeader.vue';
import CalculatorInputs from './components/CalculatorInputs.vue';
import CalculatorResult from './components/CalculatorResult.vue';

const state = reactive({
  num1: null,
  num2: null,
  operation: 'add',
});

const result = computed(() => {
  const { num1, num2, operation } = state;

  if (num1 === null || num2 === null) {
    return 'Digite ambos os números!';
  }

  switch (operation) {
    case 'add':
      return num1 + num2;
    case 'subtract':
      return num1 - num2;
    case 'multiply':
      return num1 * num2;
    case 'divide':
      return num2 !== 0 ? num1 / num2 : 'Erro: Divisão por zero';
    default:
      return 'Operação inválida!';
  }
});

const updateValues = (values) => {
  state.num1 = values.num1;
  state.num2 = values.num2;
  state.operation = values.operation;
};
</script>

<template>
  <div class="calculator container py-5">
    <div class="card shadow-lg">
      <CalculatorHeader />
      <div class="card-body">
        <CalculatorInputs
          :num1="state.num1"
          :num2="state.num2"
          :operation="state.operation"
          @updateValues="updateValues"
        />
        <CalculatorResult :result="result" />
      </div>
    </div>
  </div>
</template>

<style scoped>
.calculator {
  max-width: 600px;
  margin: auto;
}

.card {
  border-radius: 15px;
}

.card-header {
  border-radius: 15px 15px 0 0;
}

.card-body {
  padding: 30px;
}

h3 {
  margin-bottom: 10px;
}

.result p {
  font-size: 1.8em;
  font-weight: bold;
  color: #ffca28;
}
</style>