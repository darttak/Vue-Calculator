<template>
  <div class="calculator">
    <div @keyup.enter="equal" class="display">{{current || '0'}}</div>
    <button @click="clear" class="btn">C</button>
    <button @click="sign" class="btn">+/-</button>
    <button @click="percent" class="btn">%</button>
    <button @click="divide" class="btn operator">/</button>
    <button @click="append('7')" class="btn">7</button>
    <button @click="append('8')" class="btn">8</button>
    <button @click="append('9')" class="btn">9</button>
    <button @click="multiply" class="btn operator">x</button>
    <button @click="append('4')" class="btn">4</button>
    <button @click="append('5')" class="btn">5</button>
    <button @click="append('6')" class="btn">6</button>
    <button @click="minus" class="btn operator">-</button>
    <button @click="append('1')" class="btn">1</button>
    <button @click="append('2')" class="btn">2</button>
    <button @click="append('3')" class="btn">3</button>
    <button @click="plus" class="btn operator">+</button>
    <button @click="append('0')" class="btn zero">0</button>
    <button @click="dot" class="btn">.</button>
    <button @click="equal" class="btn operator">=</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      current: "",
      previous: null,
      operatorClicked: false,
      operator: null,
    };
  },
  methods: {
    clear() {
      this.current = "";
    },
    sign() {
      this.current =
        this.current.charAt(0) === "-"
          ? this.current.slice(1)
          : `-${this.current}`;
    },
    percent() {
      this.current = `${parseFloat(this.current) / 100}`;
    },
    append(number) {
      if (this.operatorClicked) {
        this.current = "";
        this.operatorClicked = false;
      }
      this.current = `${this.current}${number}`;
    },
    divide() {
      this.operator = (a, b) => a / b;
      this.previous = this.current;
      this.operatorClicked = true;
    },
    multiply() {
      this.operator = (a, b) => a * b;
      this.previous = this.current;
      this.operatorClicked = true;
    },
    minus() {
      this.operator = (a, b) => a - b;
      this.previous = this.current;
      this.operatorClicked = true;
    },
    plus() {
      this.operator = (a, b) => a + b;
      this.previous = this.current;
      this.operatorClicked = true;
    },
    dot() {
      if (this.current.indexOf(".") === -1) {
        this.append(".");
      }
    },
    equal() {
      this.current = `${this.operator(
        parseFloat(this.previous),
        parseFloat(this.current)
      )}`;
      this.previous = null;
    },
  },
};
</script>


<style scoped>
.calculator {
  margin: 0 auto;
  width: 400px;
  font-size: 50px;
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-auto-rows: minmax(50px, auto);
}
button {
  cursor: pointer;
  border-radius: 8px;
  font-size: 35px;
}
button:hover {
  background-color: rgb(179, 175, 175);
}
.display {
  font-family: digital-7;
  grid-column: 1/5;
  background-color: rgb(67, 71, 67);
  color: white;
}
.zero {
  grid-column: 1/3;
}
.btn {
  background-color: rgb(204, 201, 201);
  border: 1px solid black;
}
.operator {
  background-color: rgb(250, 163, 1);
  color: white;
}
.operator:hover {
  background-color: rgb(197, 129, 4);
}
</style>
