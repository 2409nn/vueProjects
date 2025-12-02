<template>
  <div class="app">
    <h1>Калькулятор с историей операций</h1>

    <div class="inputs">
      <input type="number" v-model.number="number1" placeholder="Число 1" />
      <input type="number" v-model.number="number2" placeholder="Число 2" />
    </div>

    <div class="operations">
      <button @click="operation = '+'">+</button>
      <button @click="operation = '-'">-</button>
      <button @click="operation = '*'">×</button>
      <button @click="operation = '/'">÷</button>
    </div>

    <h2>Результат: {{ result }}</h2>

    <h3>История:</h3>

    <ul>
      <li v-for="(item, index) in history" :key="index">{{ item }}</li>
    </ul>

    <button @click="clearHistory">Очистить историю</button>
  </div>
</template>

<script setup>
import { ref, computed, watch, onMounted } from 'vue';

const number1 = ref(0);
const number2 = ref(0);
const operation = ref('+');

const history = ref([]);

const result = computed(() => {
  switch (operation.value) {
    case '+': return number1.value + number2.value
    case '-': return number1.value - number2.value
    case '*': return number1.value * number2.value
    case '/': return number2.value !== 0 ? number1.value / number2.value : 'Ошибка'
  }
})

watch(result, (oldResult, newResult) => {
  if (oldResult === undefined) return;
  const record = `${number1.value} ${operation.value} ${number2.value} = ${oldResult}`;
  history.value.unshift(record);
  history.value = history.value.slice(0, 5);

  localStorage.setItem('calcHistory', JSON.stringify(history.value));

})

onMounted(() => {
  const saved = localStorage.getItem('calcHistory')
  if (saved) history.value = JSON.parse(saved)
})

// Очистка истории
const clearHistory = () => {
  history.value = [];
  localStorage.removeItem('calcHistory');
}
</script>

<style>
.app {
  max-width: 400px;
  margin: 40px auto;
  font-family: sans-serif;
  text-align: center;
}
.inputs input {
  width: 100px;
  margin: 5px;
}
.operations button {
  margin: 5px;
  padding: 5px 10px;
}
</style>