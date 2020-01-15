<template>
  <div id="app">
    <inputNumber @change="change" v-model="inputData"/>
    <h1>{{ msg }}</h1>
    {{inputData}}
    <label @change="change()" v-for="(event, index) in events" :key="index">
      <input type="radio" :value="event.value" v-model="valuePoint">
      <span>{{event.name}}</span>
    </label>
  </div>
</template>

<script>
import inputNumber from './components/inputNumber.vue'
export default {
  name: 'app',
  components:{
    inputNumber
  },
  data () {
    return {
      msg: 'Welcome to my Vue.js App',
      valuePoint:'',
      inputData:{
        valueFirst:'0',
        valueSecond:'0',
      },
      events:[
        {
          name:'Сложение',
          value:'add'
        },
        {
          name:'Вычитание',
          value:'deduct'
        },
        {
          name:'Умножение',
          value:'multiplication'
        },
        {
          name:'Деление',
          value:'division'
        }
      ]
    }
  },
  methods: {
    change(){
      if(this.valuePoint == 'add'){
        this.msg = this.inputData.valueFirst + this.inputData.valueSecond
      }
      if(this.valuePoint == 'deduct'){
        this.msg = this.inputData.valueFirst - this.inputData.valueSecond
      }
      if(this.valuePoint == 'multiplication'){
        this.msg = this.inputData.valueFirst * this.inputData.valueSecond
      }
      if(this.valuePoint == 'division'){
        this.msg = this.inputData.valueFirst / this.inputData.valueSecond
        if(this.inputData.valueFirst + this.inputData.valueSecond == 0 || this.msg === Infinity){
          this.msg = 'Нельзя делить на ноль'
        }
      }
    }
  },
}
</script>
<style>
  body{
    margin: 0;
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    text-align: center
  }
</style>
