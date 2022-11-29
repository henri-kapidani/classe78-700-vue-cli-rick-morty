<template>
  <div class="container">
    <PageHeader :results-for="searchString" />
    <PageMain @search="search" />
    <PageFooter />
  </div>
</template>

<script>
// TODO: import bootstrap script
import PageHeader from '@/components/PageHeader.vue';
import PageMain from '@/components/PageMain.vue';
import PageFooter from '@/components/PageFooter.vue';

export default {
  components: {
    PageHeader,
    PageMain,
    PageFooter,
  },
  data() {
    return {
      searchString: '',
    };
  },
  methods: {
    search(data) {
      this.searchString = data;
    },
  },
};
</script>

<style lang="scss">
@import "~bootstrap/scss/bootstrap";
@import url('https://fonts.googleapis.com/css2?family=Lato&display=swap');

body {
  font-family: 'Lato', sans-serif;
}
</style>
