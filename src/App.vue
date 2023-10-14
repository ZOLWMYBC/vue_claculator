<template>
  <div class="App">
    <YyHeader>{{ equation }}</YyHeader>
    <YyFooter>
      <YyBaseButton id="btn-ac" @click="clear()">AC</YyBaseButton>
      <YyBaseButton id="btn-/" @click="negative()">+/-</YyBaseButton>
      <YyBaseButton id="btn-%" @click="percent()">%</YyBaseButton>
      <YyBaseButton id="btn-d" @click="getStr('/')">/</YyBaseButton>
      <YyBaseButton id="btn-7" @click="getStr('7')">7</YyBaseButton>
      <YyBaseButton id="btn-8" @click="getStr('8')">8</YyBaseButton>
      <YyBaseButton id="btn-9" @click="getStr('9')">9</YyBaseButton>
      <YyBaseButton id="btn-x" @click="getStr('x')">x</YyBaseButton>
      <YyBaseButton id="btn-4" @click="getStr('4')">4</YyBaseButton>
      <YyBaseButton id="btn-5" @click="getStr('5')">5</YyBaseButton>
      <YyBaseButton id="btn-6" @click="getStr('6')">6</YyBaseButton>
      <YyBaseButton id="btn--" @click="getStr('-')">-</YyBaseButton>
      <YyBaseButton id="btn-1" @click="getStr('1')">1</YyBaseButton>
      <YyBaseButton id="btn-2" @click="getStr('2')">2</YyBaseButton>
      <YyBaseButton id="btn-3" @click="getStr('3')">3</YyBaseButton>
      <YyBaseButton id="btn-+" @click="getStr('+')">+</YyBaseButton>
      <YyBaseButton id="btn-0" @click="getStr('0')">0</YyBaseButton>
      <YyBaseButton @click="getStr('.')">.</YyBaseButton>
      <YyBaseButton @click="calculate">=</YyBaseButton>
    </YyFooter>
  </div>
</template>

<script>
import YyHeader from './components/YyHeader.vue'
import YyFooter from './components/YyFooter.vue'
import YyBaseButton from './components/YyBaseButton.vue'
export default {
  components: {
    YyHeader,
    YyFooter,
    YyBaseButton
  },
  data() {
    return {
      equation: '0',
      isDecimalPoint: false,  //防止出现多个小数点
      isEnter: false,
      isTailOperater: false
    }
  },
  methods: {
    //判断是否是运算符
    isOperator(e) {
      return ['+', '-', 'x', '/'].indexOf(e) > -1
    },
    //判断输入的是否是数字
    isNumber(e) {
      return e > -1 && e < 10 ? true : false
    },
    //输入数字
    getStr(e) {
      if (this.isTailOperater && !this.isOperator(e)) {
        this.isTailOperater = false
      }
      if (this.isEnter && this.isNumber(e)) {
        this.equation = '0'
      }
      this.isEnter = false
      if (this.isNumber(e)) {
        if (this.equation === '0') { this.equation = e }
        else { this.equation += e }
      }
      //防止数字中出现多个"."
      if (e === '.' && !this.isDecimalPoint) {
        this.equation += e
        this.isDecimalPoint = true
      }
      if (this.isOperator(e) && !this.isTailOperater) {
        this.equation += e
        this.equation = this.equation.replace(new RegExp('x', 'g'), '*')
        this.isTailOperater = true
        this.isDecimalPoint = false
      }
    },
    calculate() {
      this.equation = parseFloat(eval(this.equation).toFixed(9)).toString()
      this.isEnter = true
      this.isDecimalPoint = false
    },
    percent() {
      if (!this.isTailOperater)
        this.equation = this.equation + '*0.01'
      this.calculate()
    },
    negative() {
      if (!this.isTailOperater && this.equation !== '0')
        this.equation = this.equation + '*(-1)'
      this.calculate()
    },
    clear() {
      this.equation = '0'
      this.isDecimalPoint = false
      this.isEnter = false
      this.isTailOperater = false
    }
  },
}
</script>

<style>
.App {
  text-align: center;
}

#btn-0 {
  flex: 2 40%;
}
</style>
