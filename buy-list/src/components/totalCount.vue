<script>

export default {
  props: {
    list: {
      type: Array,
      default: () => []
    }
  },
}
</script>

<template>
  <div class="total">
    <div class="total__elements-count">
      <span>Всего товаров: </span><p style="display: inline">{{ list.length }} шт.</p>
    </div>
  </div>
</template>

<style scoped lang="scss">
.total {
  text-align: center;
  margin-top: 20px;
}
</style>