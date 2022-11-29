<template>
  <div>
    <SearchBar @search="search" />
    <!--
      se filtriamo in locale leghiamo il template ad arrFiltered (array filtrato)
      altrimenti usiamo arrCharacters (array originale)
    -->
    <div
      v-if="arrFiltered"
      class="row row-cols-4 g-5"
    >
      <CardCharacter
        v-for="character in arrFiltered"
        :key="character.id"
        :img-url="character.image"
        :name="character.name"
        :origin="character.origin.name"
        :species="character.species"
      />
    </div>
    <div v-else>
      Loading ...
    </div>
  </div>
</template>

<script>
import axios from 'axios';
import CardCharacter from '@/components/CardCharacter.vue';
import SearchBar from '@/components/SearchBar.vue';

export default {
  name: 'PageMain',
  components: {
    CardCharacter,
    SearchBar,
  },
  data() {
    return {
      arrCharacters: null,
      urlApi: 'https://rickandmortyapi.com/api/character', // TODO: pagination
      searchString: '', // serve se filtriamo in locale
    };
  },
  computed: { // serve se filtriamo in locale
    arrFiltered() {
      if (this.arrCharacters) {
        return this.arrCharacters.filter(
          // eslint-disable-next-line
          (objCharacter) => objCharacter.name.trim().toLowerCase().includes(this.searchString.trim().toLowerCase()),
        );
      }
      return null;
    },
  },
  created() {
    // scaricare i dati
    axios.get(this.urlApi)
      .then((axiosResponse) => {
        console.log(axiosResponse);
        this.arrCharacters = axiosResponse.data.results;
      });
  },
  methods: {
    search(searchString) {
      this.searchString = searchString; // serve se filtriamo in locale
      this.$emit('search', searchString);

      // per filtrare i risultati chiedendoli al server
      // axios.get(this.urlApi, {
      //   params: {
      //     name: searchString,
      //   },
      // })
      //   .then((axiosResponse) => {
      //     console.log(axiosResponse);
      //     this.arrCharacters = axiosResponse.data.results;
      //   })
      //   .catch((error) => {
      //     console.log(error);
      //     if (error.response.status === 404
      //       && error.response.data.error === 'There is nothing here'
      //     ) {
      //       this.arrCharacters = [];
      //     }
      //   });
    },
  },
};
</script>

<style lang="scss" scoped>
</style>
