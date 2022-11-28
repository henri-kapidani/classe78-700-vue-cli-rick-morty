<template>
  <div class="col">
    <div class="contents text-center">
      <img
        :src="imgUrl"
        :alt="name"
        class="img-fluid rounded-circle"
      >
      <h2 class="name">
        {{ name }}
      </h2>
      <div class="origin">
        {{ origin }}
      </div>
      <div class="species">
        {{ species }}
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'CardCharacter',
  props: {
    imgUrl: String,
    name: String,
    origin: String,
    species: String,
  },
};
</script>

<style lang="scss" scoped>

</style>
