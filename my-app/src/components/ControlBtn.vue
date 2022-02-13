<script setup lang="ts">

const emit = defineEmits<{
    (event: 'inc-count', inc: number): void;
    (event: 'reset-count'): void;
}>()

</script>

<template>
  <div>
    <button @click="emit('inc-count', 2)">
        Inc.
    </button> 
    <button @click="emit('reset-count')">
        Reset
    </button>
  </div>
</template>
