<script>
export default {
  props: {
    list: {
      type: Array,
      default: () => []
    }
  }
}
</script>

<template>
  <div class="list">
    <p class="empty-state" v-if="list.length === 0">В списке ничего нет</p>
    <ul class="list__items" v-else v-for="item in list">
      <li class="list__item">
        <p class="list__item-title">{{ item.title }}</p>
<!--        <p class="list__item-price"><span>$</span>{{ item.price }}</p>-->
      </li>
    </ul>
  </div>
</template>

<style scoped lang="scss">
.list {
  border: 1px solid #ccc;
  border-radius: 12px;
  width: 80%;
  min-height: 500px;
  margin: 0 auto;

  .empty-state {
    color: #727272;
    font-weight: 500;
    margin: auto;
    text-align: center;
    position: relative;
    top: 200px;
    user-select: none;
  }

  .list__item {
    list-style: none;
    border-bottom: 1px solid #ccc;
    padding: 10px 20px;
    display: flex;
    justify-content: center;
  }
}
</style>