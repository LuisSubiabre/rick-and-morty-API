<template>
  <Search @search="onSearch" />
  <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-4">
    <Card v-for="(card, index) in displayedCards" :key="index" :card="card" />
  </div>
</template>

<script>
import Card from './Card.vue';
import Search from './Search.vue';


export default {
  name: 'CardList',
  components: {
    Card,
    Search
  },
  data() {
    return {
      cards: [],
      searchTerm: '',
      displayedCards: [] // Nueva propiedad de datos
    };
  },
  computed: {
    filteredCards() {
      return this.cards.filter(card =>
        card.title.toLowerCase().includes(this.searchTerm.toLowerCase())
      );

    }
  },
  methods: {
    onSearch(term) {
      this.searchTerm = term;
      this.updateDisplayedCards();
    },
    updateDisplayedCards() {
      this.displayedCards = this.filteredCards;
    }
  },
  mounted() {
    // Llamada a la API
    fetch('https://rickandmortyapi.com/api/character')
      .then(response => response.json())
      .then(data => {
        // Mapea los resultados
        this.cards = data.results.map(character => ({
          id: character.id,
          imageUrl: character.image,
          title: character.name,
          description: character.species
        }));
        this.updateDisplayedCards(); // Inicializa la lista de tarjetas mostradas
      })
      .catch(error => {
        console.log('Error al obtener datos de la API: ', error);
      });
  }
};
</script>