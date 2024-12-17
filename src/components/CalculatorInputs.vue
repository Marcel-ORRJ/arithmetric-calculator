<script setup>
import { ref } from 'vue';

const props = defineProps({
    num1: Number,
    num2: Number,
    operation: String,
});

const emit = defineEmits(['updateValues']);

const num1 = ref(props.num1);
const num2 = ref(props.num2);
const operation = ref(props.operation);

const emitUpdate = () => {
    emit('updateValues', { num1: num1.value, num2: num2.value, operation: operation.value });
};
</script>

<template>
    <div class="row g-3 align-items-center justify-content-center">
        <div class="col-12 col-md-3">
            <input
            v-model.number="num1"
            type="number"
            class="form-control"
            placeholder="Digite o 1º número"
            @input="emitUpdate"
            />
        </div>
        <div class="col-12 col-md-2">
            <select v-model="operation" class="form-select" @change="emitUpdate">
            <option value="add">+</option>
            <option value="subtract">-</option>
            <option value="multiply">×</option>
            <option value="divide">÷</option>
            </select>
        </div>
        <div class="col-12 col-md-3">
            <input
            v-model.number="num2"
            type="number"
            class="form-control"
            placeholder="Digite o 2º número"
            @input="emitUpdate"
            />
        </div>
    </div>
</template>
