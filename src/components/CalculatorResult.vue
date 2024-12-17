<script setup>
    const props = defineProps(['result']);
</script>

<template>
    <div class="mt-4 text-center">
        <h3 class="text-primary">Resultado:</h3>
        <p class="fs-4 fw-bold text-warning">{{ result }}</p>
    </div>
</template>
