<template>
  <div class="calculator">
    <div class="display">{{ display }}</div>
    <div class="buttons">
      <button @click="clear">C</button>
      <button @click="appendToDisplay('7')">7</button>
      <button @click="appendToDisplay('8')">8</button>
      <button @click="appendToDisplay('9')">9</button>
      <button @click="appendToDisplay('+')">+</button>
      <button @click="appendToDisplay('4')">4</button>
      <button @click="appendToDisplay('5')">5</button>
      <button @click="appendToDisplay('6')">6</button>
      <button @click="appendToDisplay('-')">-</button>
      <button @click="appendToDisplay('1')">1</button>
      <button @click="appendToDisplay('2')">2</button>
      <button @click="appendToDisplay('3')">3</button>
      <button @click="appendToDisplay('*')">*</button>
      <button @click="appendToDisplay('0')">0</button>
      <button @click="appendToDisplay('.')">.</button>
      <button @click="calculate">=</button>
      <button @click="appendToDisplay('/')">/</button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      display: '',
    };
  },
  methods: {
    appendToDisplay(value) {
      this.display += value;
    },
    clear() {
      this.display = '';
    },
    calculate() {
      try {
        this.display = eval(this.display);
      } catch (error) {
        this.display = 'Error';
      }
    },
  },
};
</script>

<style scoped>
.calculator {
  width: 300px;
  margin: 0 auto;
  text-align: center;
  background-color: #444;
  padding: 10px;
  border-radius: 5px;
}

.display {
  background: #222;
  height: 50px;
  line-height: 50px;
  font-size: 24px;
  color: #fff;
}

.buttons {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
}

button {
  background: #333;
  color: #fff;
  border: none;
  height: 50px;
  font-size: 18px;
  transition: background 0.2s;
}

button:hover {
  background: #555;
}

.operator {
  background: #f44336; /* Red for operators */
}

.operator:hover {
  background: #d32f2f; /* Darker red on hover */
}
</style>