<script setup>
import BlogPost from './components/BlogPost.vue'
import PaginatePost from './components/PaginatePost.vue'
import LoadingSpinner from './components/LoadingSpinner.vue'
import { ref, onMounted } from 'vue';

const posts = ref([]);

const postXpage = 5;

const inicio = ref(0);
const fin = ref(postXpage);

const favorito = ref('');

const loading = ref(true);

onMounted(async () => {
  try {

    const res = await fetch('https://jsonplaceholder.typicode.com/posts')
    posts.value = await res.json()

  } catch (error) {
    console.log(error)
  } finally {
    loading.value = false
  }
})



const cambiarFavorito = (title) => {
  favorito.value = title
}

const next = () => {
  inicio.value += postXpage
  fin.value += postXpage
}

const prev = () => {
  inicio.value -= postXpage
  fin.value -= postXpage
}

</script>

<!-- <script>

export default {
  data() {
    return {
      counter: 0
    }
  },
  methods: {
    increment() {
      this.counter++
    }
  }
}

</script> -->

<template>
  <LoadingSpinner v-if="loading" />
  <div class="container" v-else>
    <h2 class="mt-5">Mi Post favorito: <span class="text-primary">{{ favorito }}</span></h2>

    <!-- <button @click="next">Prueba Next</button>
    <button @click="prev">Prueba Prev</button> -->

    <PaginatePost @next="next" :maxLength="posts.length" :inicio="inicio" :fin="fin" @prev="prev" />
    <BlogPost v-for="post in posts.slice(inicio, fin)" :key="post.id" :title="post.title" :id="post.id"
      :body="post.body" :cambiarFavorito="cambiarFavorito">
    </BlogPost>

  </div>

</template>
<!-- <script>
import { ref } from 'vue';

export default {
  // Inicialización de variables
  setup() {
    const counter = ref(0)
    const increment = () => {
      counter.value++
    } 
    // Exportación de variables
    return {
      counter,
      increment
    }
  }
}
</script> -->

<!-- <script setup></script> -->