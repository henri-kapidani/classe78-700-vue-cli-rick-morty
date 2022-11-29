<template>
  <div>
    <h1 class="text-center">
      {{ resultsFor ? 'Risultati per: ' + resultsFor : 'Rick and Morty App' }}
    </h1>
  </div>
</template>

<script>
export default {
  name: 'PageHeader',
  props: {
    resultsFor: String,
  },
};
</script>

<style lang="scss" scoped>

</style>
