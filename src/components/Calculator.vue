<template>
  <div class="calculator">
    <div class="display">{{ current || 0 }}</div>
    <div @click="clear()">C</div>
    <div @click="sign()">+/-</div>
    <div @click="percent()">%</div>
    <div class="operator" @click="divide()">÷</div>
    <div @click="append(7)">7</div>
    <div @click="append(8)">8</div>
    <div @click="append(9)">9</div>
    <div class="operator" @click="times()">*</div>
    <div @click="append(4)">4</div>
    <div @click="append(5)">5</div>
    <div @click="append(6)">6</div>
    <div class="operator" @click="minus()">-</div>
    <div @click="append(1)">1</div>
    <div @click="append(2)">2</div>
    <div @click="append(3)">3</div>
    <div class="operator" @click="add()">+</div>
    <div class="zero" @click="append(0)">0</div>
    <div @click="dot()">.</div>
    <div class="operator" @click="equal()">=</div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      previous: null,
      current: '',
      operator: null,
      operatorClicked: false,
    };
  },
  methods: {
    clear() {
      this.current = '';
      console.log('Clear');
    },
    sign() {
      this.current = this.current.charAt(0) === '-' ? this.current.slice(1) : `-${this.current}`;
    },
    percent() {
      this.current = `${parseFloat(this.current) / 100}`;
    },
    append(number) {
      if (this.operatorClicked) {
        this.clear;
        this.operatorClicked = false;
      }
      this.current = `${this.current}${number}`;
    },
    dot() {
      if (this.current.indexOf('.') === -1) {
        this.append('.');
        console.log('add Dot');
      }
    },

    setPrevious() {
      this.previous = this.current;
      this.clear();
      this.operatorClicked = true;
    },

    divide() {
      console.log('divide');
      this.setPrevious();
      this.operator = (a, b) => a / b;
    },
    times() {
      console.log('times');
      this.setPrevious();
      this.operator = (a, b) => a * b;
    },
    minus() {
      console.log('minus');
      this.setPrevious();
      this.operator = (a, b) => a - b;
    },
    add() {
      console.log('add');
      this.setPrevious();
      this.operator = (a, b) => a + b;
    },
    equal() {
      console.log('equal');

      this.current = `${this.operator(parseFloat(this.previous), parseFloat(this.current))}`;
      this.previous = null;
    },
  },
};
</script>

<style lang="scss" scoped>
.calculator {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 300px;
  margin: 0 auto;
  border-radius: 1rem;
  overflow: hidden;
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-auto-rows: 1fr;
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.12), 0 1px 2px rgba(0, 0, 0, 0.24);
  padding: 0.85rem 0.25rem;
  background-color: #222;
  grid-gap: 0.3rem;
  color: #f2f2f2;
  div {
    padding: 1rem;
    font-weight: 700;
    border: 0.1rem solid #f2f2f2;
    border-radius: 0.2rem;
    background-color: #313131;
    align-self: center;
    cursor: pointer;
    text-align: center;
  }
  .operator {
    background-color: #f79a0a;
  }
  .display {
    grid-column: 1 / 5;
    background-color: #222;
    color: #f2f2f2;
    padding: 1rem;
    cursor: default;
  }
  .zero {
    grid-column: 1 /3;
  }
}
</style>
