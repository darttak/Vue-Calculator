<template>
  <div class="calculator">
    <input type="text" class="display" v-model="result" placeholder="0" />
    <button @click="clear" class="btn">C</button>
    <button @click="input(num)" class="btn" v-bind:key="num" v-for="num in numbers">{{num}}</button>
    <button @click="input(op)" class="btn operator" v-bind:key="op" v-for="op in operations">{{op}}</button>
    <button @click="equal" class="btn operator">=</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      numbers: [1, 2, 3, 4, 5, 6, 7, 8, 9, 0],
      result: "",
      operations: ["+", "-", "*", "/"],
    };
  },
  methods: {
    input: function (char) {
      this.result += char;
    },
    clear: function () {
      this.result = "";
    },
    equal: function () {
      this.result = eval(this.result);
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
  font-size: 35px;
  text-align: right;
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
