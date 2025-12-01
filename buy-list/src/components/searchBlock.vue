<script>
export default {
  data() {
    return {
      title: '',
    }
  },
  props: {
    list: {
      type: Array,
      default: () => []
    }
  }
}
</script>

<template>
  <div class="search">
    <form>
      <input type="text" class="search__input-text" placeholder="Введите товар..." v-model="title">
      <input type="button" class="search__input-button" value="Добавить" @click="list.push({'title': title})">
    </form>
  </div>
</template>

<style scoped lang="scss">
.search {
  display: flex;
  flex-direction: row;
  justify-content: center;

  &__input-text {
    padding: 12px 20px;
    border-radius: 6px;
    border: 1px solid #ccc;
  }

  &__input-button {
    background-color: #3978f6;
    color: white;
    border-radius: 6px;
    border: 1px solid #1f66f3;
    padding: 12px 20px;
    margin: 10px;
  }
}
</style>