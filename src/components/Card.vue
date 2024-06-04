<template>
  <div class="bg-white rounded-lg shadow-md p-4">
    <img :src="card.imageUrl" alt="Card image" class="w-full h-48 object-cover mb-4 rounded-md">
    <h2 class="text-gray-600 text-xl font-semibold mb-2">{{ card.title }}</h2>
    <p class="text-gray-600">{{ card.description }}</p>
    <button class="mt-4 bg-blue-500 hover:bg-blue-600 text-white px-4 py-2 rounded-md">Ver más</button>
  </div>
</template>

<script>
export default {
  name: 'Card',
  props: {
    card: {
      type: Object,
      required: true
    }
  }
};
</script>

<style scoped>
/* Puedes agregar estilos adicionales aquí */
</style>