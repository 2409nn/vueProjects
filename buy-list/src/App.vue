<script>
  import search from "./components/searchBlock.vue";
  import heading from "./components/heading.vue";
  import listBlock from "./components/listBlock.vue"
  import totalCount from "./components/totalCount.vue";
  export default {

    data() {
      return {
        products: [
          {"title": "Яблоко"},
          {"title": "Чайник"},
        ]
      }
    },

    components: {
      search,
      heading,
      listBlock,
      totalCount
    }
  }
</script>

<template>
  <heading />
  <search :list="products" />
  <list-block :list="products" />
  <total-count :list="products" />
</template>

<style></style>
