<template>
  <div class="p-8 bg-white bg-opacity-10 rounded-lg shadow-lg backdrop-blur-md">
    <h1 class="text-8xl font-extrabold mb-4 animate-bounce">404</h1>
    <p class="text-2xl font-light mb-6">Oops! The page you're looking for doesn't exist.</p>
    <i class="pi pi-exclamation-circle text-5xl mb-6"></i>
    <RouterLink to="/" class="px-6 py-3 bg-gradient-to-r from-green-400 to-blue-500 
    text-white font-semibold rounded-lg shadow-md hover:from-green-500 hover:to-blue-600 
    transition-transform transform hover:scale-105">
      Take Me Home
    </RouterLink>
  </div>

</template>

<script setup lang="ts">

</script>

<style scoped>
/* Add some subtle animations */
@keyframes bounce {

  0%,
  100% {
    transform: translateY(0);
  }

  50% {
    transform: translateY(-10px);
  }
}

.animate-bounce {
  animation: bounce 1.5s infinite;
}
</style>