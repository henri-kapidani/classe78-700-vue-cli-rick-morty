<template>
  <div>
    <label for="s">
      <input
        id="s"
        v-model="searchString"
        type="text"
        name="s"
        @keyup.enter="search"
      >
    </label>
    <button @click="search">
      Cerca
    </button>
  </div>
</template>

<script>
export default {
  name: 'SearchBar',
  data() {
    return {
      searchString: '',
    };
  },
  methods: {
    search() {
      this.$emit('search', this.searchString);
    },
  },
};
</script>

<style lang="scss" scoped>

</style>
