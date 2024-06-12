<template>
  <div
    v-if="show"
    class="fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center"
  >
    <div class="flex flex-col justify-center items-center bg-white p-4 rounded-md w-96">
      <div class="mb-4">
        <h2 class="text-lime-800 text-xl font-semibold">{{ card.title }}</h2>
        
      </div>
      <img
        :src="card.imageUrl"
        alt="Card image"
        class="size-48 object-cover mb-4 rounded-full "
      />
      <span class="text-lime-800">Specie: {{ card.description }}</span>
      <span class="text-lime-800" v-if="card.status ==='Alive'">Status: {{ card.status }} 🟢</span>
        <span class="text-lime-800" v-else-if="card.status ==='Dead'">Status: {{ card.status }} 🔴</span>
        <span class="text-lime-800" v-else>Status: {{ card.status }} ⚪️</span> <!-- Default icon for other statuses -->
      <button @click="close" class="mt-4 bg-lime-500 hover:bg-lime-600 text-white px-4 py-2 rounded-md">Cerrar</button>
    </div><
  </div>
</template>

<script>
export default {
  name: "Modal",
  props: {
    show: {
      type: Boolean,
      required: true,
    },
    card: {
      type: Object,
      required: true,
    },
  },
  methods: {
    close() {
      this.$emit("close");
    },
  },
};
</script>

<style scoped>
/* Agregar cualquier estilo adicional si es necesario */
</style>
