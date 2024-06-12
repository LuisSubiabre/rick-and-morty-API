<template>
  <div class="bg-white rounded-lg shadow-md p-4">
    <img :src="card.imageUrl" alt="Card image" class="w-full h-48 object-cover mb-4 rounded-md">
    <h2 class="text-gray-600 text-xl font-semibold mb-2">{{ card.title }}</h2>
    <p class="text-gray-600">{{ card.description }}</p>
    <button @click="viewMore" class="mt-4 bg-lime-500 hover:bg-lime-600 text-white px-4 py-2 rounded-md">Ver más</button>
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
  },
  methods: {
    viewMore(){
      this.$emit('view-more', this.card);
    }
  }
};
</script>