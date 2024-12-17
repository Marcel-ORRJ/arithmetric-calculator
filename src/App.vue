<script setup>
import { reactive, computed } from 'vue';

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
</script>

<template>
  <div class="calculator container py-5">
    <div class="card shadow-lg">
      <div class="card-header text-center bg-primary text-white">
        <h2>Calculadora Aritmética</h2>
      </div>
      <div class="card-body">
        <div class="row g-3 align-items-center justify-content-center">
          <div class="col-12 col-md-3">
            <input
              v-model.number="state.num1"
              type="number"
              class="form-control"
              placeholder="Digite o 1º número"
            />
          </div>
          <div class="col-12 col-md-2">
            <select v-model="state.operation" class="form-select">
              <option value="add">+</option>
              <option value="subtract">-</option>
              <option value="multiply">×</option>
              <option value="divide">÷</option>
            </select>
          </div>
          <div class="col-12 col-md-3">
            <input
              v-model.number="state.num2"
              type="number"
              class="form-control"
              placeholder="Digite o 2º número"
            />
          </div>
        </div>
        <div class="mt-4 text-center">
          <h3 class="text-primary">Resultado:</h3>
          <p class="fs-4 fw-bold text-warning">{{ result }}</p>
        </div>
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
</style>
