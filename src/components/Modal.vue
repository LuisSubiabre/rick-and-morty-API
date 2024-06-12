<template>
  <div
    v-if="show"
    class="fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center"
  >
    <div class="bg-white p-4 rounded-md w-1/2">
      <div class="flex justify-between items-center mb-4">
        <h2 class="text-xl font-semibold">{{ card.title }}</h2>
        <button @click="close" class="text-red-500">X</button>
      </div>
      <img
        :src="card.imageUrl"
        alt="Card image"
        class="w-full h-28 object-cover mb-4 rounded-md"
      />
      <p>{{ card.description }}</p>
    </div>
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
