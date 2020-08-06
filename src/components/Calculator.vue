<template>
  <div class="calculator">
    <div class="display">{{ current || '0'  }}</div>
    <div @click="clear" class="btn b">C</div>
    <div @click="sign" class="btn b">+/-</div>
    <div @click="percent" class="btn b">%</div>
    <div @click="divide" class="btn operator">÷</div>
    <div @click="append('7')" class="btn">7</div>
    <div @click="append('8')" class="btn">8</div>
    <div @click="append('9')" class="btn">9</div>
    <div @click="multiply" class="btn operator">x</div>
    <div @click="append('4')" class="btn">4</div>
    <div @click="append('5')" class="btn">5</div>
    <div @click="append('6')" class="btn">6</div>
    <div @click="subtract" class="btn operator">-</div>
    <div @click="append('1')" class="btn">1</div>
    <div @click="append('2')" class="btn">2</div>
    <div @click="append('3')" class="btn">3</div>
    <div @click="add" class="btn operator">+</div>
    <div @click="append('0')" class="btn two-span z">0</div>
    <div @click="dot" class="btn">.</div>
    <div @click="equal" class="btn operator e">=</div>
  </div>
</template>

<script>

export default {
  name: 'Calculator',
  data() {
    return {
      previous: null,
      current: '',
      operator: null,
      operatorClicked: false
    }
  },
  methods: {
    clear() {
      this.current = ''
    },
    sign() {
      this.current = this.current.charAt(0) === '-' ? this.current.slice(1) : `-${this.current}`
    },
    percent() {
      this.current = `${parseFloat(this.current) / 100}`
    },
    append(num) {
      if (this.operatorClicked) {
        this.current = ''
        this.operatorClicked = false
      }
      this.current = `${this.current}${num}`
    },
    dot() {
      if (this.current.indexOf('.') === -1) {
        this.append('.')
      }
    },
    setPrevious() {
      this.previous = this.current
      this.operatorClicked = true
    },
    divide() {
      this.operator = (a, b) => a / b;
      this.setPrevious()
    },
    multiply() {
      this.operator = (a, b) => a * b;
      this.setPrevious()
    },
    subtract() {
      this.operator = (a, b) => a - b;
      this.setPrevious()
    },
    add() {
      this.operator = (a, b) => a + b;
      this.setPrevious()
    },
    equal() {
      this.current = `${this.operator(
          parseFloat(this.previous),
          parseFloat(this.current)
      )}`
      this.previous = null
    }
  }
}
</script>

<style scoped>
.calculator {
  width: 300px;
  margin: 0 auto;
  font-size: 40px;
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-auto-rows: minmax(50px, auto);
}

.display {
  grid-column: span 4;
  background-color: #505050;
  color: white;
  text-align: right;
  padding-right: 25px;
  padding-top: 40px;
  border-radius: 16px 16px 0 0;
}

.two-span {
  grid-column: span 2;
}

.btn {
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
  transition: 0.1s;
  cursor: pointer;
  background-color: rgba(80, 80, 80, .75);
  border: 0.1px solid #1C1C1C;
  color: white;
}

.btn:active {
  background-color: white;
}

.operator {
  background-color: #FF9500;
  color: white;
}

.e {
  border-radius: 0 0 16px 0;
}

.z {
  border-radius: 0 0 0 16px;
}

.b {
  background-color: #505050;
}
</style>
