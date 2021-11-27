<template>
  <div>
    <h1>{{ msg }}</h1>
    
    <input v-model="num1" placeholder="Enter a number" type="number">

    <select v-model="operator">
      <option disabled value="">Please select the operation to perform</option>
      <option>+</option>
      <option>-</option>
      <option>/</option>
      <option>*</option>
    </select>

    <input v-model="num2" placeholder="Enter a number" type="number">

    <button v-on:click="calculate()">Calculate</button>

    <br/>

    <h3 v-if="!loading">Result: {{ this.result }}</h3>
    <h3 v-if="loading">Calculating ..</h3>
    
  </div>
</template>

<script>
export default {
  data() {
    return {
      result: 0,
      num1: 0,
      num2: 0,
      operator: '',
      loading: false
    }
  },
  props: {
    msg: String
  },
  updated() {
    setTimeout(() => {
        this.loading = false;
    }, 5000);
  },
  methods: {
    calculate: function () {
      this.loading = true;
      switch (this.operator) {
        case '+':
          this.result = parseInt(this.num1) + parseInt(this.num2);
          break;
        case '-':
          this.result = parseInt(this.num1) - parseInt(this.num2);
          break;
        case '/':
          this.result = parseInt(this.num1) / parseInt(this.num2);
          break;
        case '*':
          this.result = parseInt(this.num1) * parseInt(this.num2);
          break;
      }
    }
  },
}
</script>