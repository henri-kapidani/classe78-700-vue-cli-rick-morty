<template>
  <div>
    <div
      v-if="arrCharacters"
      class="row row-cols-4 g-5"
    >
      <CardCharacter
        v-for="character in arrCharacters"
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

export default {
  name: 'PageMain',
  components: {
    CardCharacter,
  },
  data() {
    return {
      arrCharacters: null,
      urlApi: 'https://rickandmortyapi.com/api/character', // TODO: pagination
    };
  },
  created() {
    // scaricare i dati
    axios.get(this.urlApi)
      .then((axiosResponse) => {
        console.log(axiosResponse);
        this.arrCharacters = axiosResponse.data.results;
      });
  },
};
</script>

<style lang="scss" scoped>
</style>
