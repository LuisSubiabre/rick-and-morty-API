<template>
  <div>
    <input
      type="text"
      v-model="searchTerm"
      placeholder="Buscar..."
      class="mb-4 w-full px-4 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-blue-500"
    @input="onInput" />
  </div>
</template>

<script>
export default {
  name: 'Search',
  data() {
    return {
      searchTerm: ''
    };
  },
  methods: {
    onInput() {
      this.$emit('search', this.searchTerm);
    }
  }
};
</script>