<template>
  <Search @search="onSearch" />
  <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-4">
    <Card v-for="(card, index) in displayedCards" :key="index" :card="card" @view-more="showModal" />
  </div>
    <Modal v-if="selectedCard" :show="isModalVisible" :card="selectedCard" @close="hideModal" />
</template>

<script>
import Card from './Card.vue';
import Search from './Search.vue';
import Modal from './Modal.vue'

export default {
  name: 'CardList',
  components: {
    Card,
    Search,
    Modal
  },
  data() {
    return {
      cards: [],
      searchTerm: '',
      displayedCards: [],
      isModalVisible: false,
      selectedCard: null
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
    },
    showModal(card) {
      this.selectedCard = card;
      this.isModalVisible = true;
    },
    hideModal(){
      this.isModalVisible = false;
      this.selectedCard = null;
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
          description: character.species,
          status: character.status,
          location: character.location.name
        }));
        this.updateDisplayedCards(); // Inicializa la lista de tarjetas mostradas
      })
      .catch(error => {
        console.log('Error al obtener datos de la API: ', error);
      });
  }
};
</script>