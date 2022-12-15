<script setup>

// defineProps(['title', 'id', 'content']);
defineProps({
    // String, Number, Boolean, Array, Object, Date, Function, Symbol
    title: String,
    id: Number,
    body: {
        type: String,
        default: 'Sin descripción...'
    },
    cambiarFavorito: Function

});

// const emit = defineEmits(['cambiarFavoritoNombre'])

</script>
<template>
    <div class="card shadow mb-2">
        <div class="card-body">
            <h5 class="card-title">
                {{ id }} - {{ title }}
            </h5>
            <p>{{ body }}</p>
            <button class="btn btn-outline-primary" @click="cambiarFavorito(title)">
                Favorito
            </button>
        </div>
    </div>
</template>
