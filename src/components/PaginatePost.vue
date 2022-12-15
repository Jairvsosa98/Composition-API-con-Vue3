<script setup>

defineProps(['inicio', 'fin', 'maxLength'])

const emit = defineEmits(['next', 'prev'])
    
</script>
<template>
    <div class="btn-group mb-2 mt-2" role="group" aria-label="Basic outlined example">
        <button @click="emit('prev')" :disabled="inicio === 0" type="button" class="btn btn-outline-primary">Preview</button>        
        <button @click="emit('next')" :disabled="fin >= maxLength" class="btn btn-outline-primary">Next</button>
    </div>
</template>