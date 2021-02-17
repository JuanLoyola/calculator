<template>
  <div class="container">
    <div class="calculator">
    <div class="screen">
      <div id="result">{{valorCorriente || 0}}</div>
    </div>
    <div class="keycaps">
        <div class="numbers">
          <div>
            <button id="n1" @click="enviarNumero(7)">7</button>
            <button id="n2" @click="enviarNumero(8)">8</button>
            <button id="n3" @click="enviarNumero(9)">9</button>
          </div>
          <div>
            <button id="n4" @click="enviarNumero(4)">4</button>
            <button id="n5" @click="enviarNumero(5)">5</button>
            <button id="n6" @click="enviarNumero(6)">6</button>
          </div>
          <div>
            <button id="n7" @click="enviarNumero(1)">1</button>
            <button id="n8" @click="enviarNumero(2)">2</button>
            <button id="n9" @click="enviarNumero(3)">3</button>
          </div>
          <div>
          <button id="n0" @click="enviarNumero(0)">0</button>
          <button id="clear" @click="limpiar">C</button>

          </div>
        </div>
        <div class="op">
          <button id="s" @click="sumar('+')">+</button>
          <button id="r" @click="restar('-')">-</button>
          <button id="d" @click="dividir('÷')">÷</button>
          <button id="m" @click="multiplicar('*')">x</button>
        </div>
    </div>
    <div class="result btn">
      <button id="result-btn" @click="resultado">=</button>
    </div>
    <div class="container-sign">
      <a class="sign" href="https://www.linkedin.com/in/loyolajuan" target="_blank">Developed by Juan Loyola</a>
    </div>
    </div>
  </div>
</template>

<style lang="scss">
  .container {
    width: 100%;
    height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
    font-family: sans-serif, Arial, Helvetica;
    background-image: url('../assets/bg2.png');
    background-size: cover;
    background-repeat: no-repeat;

    .calculator {
      background-color: #f2f5f5;
      border-radius: 9px;
      -webkit-box-shadow: -2px 4px 6px -1px rgba(133,133,133,1);
      -moz-box-shadow: -2px 4px 6px -1px rgba(133,133,133,1);
      box-shadow: -2px 4px 6px -1px rgba(133,133,133,1);
    }
    .keycaps {
      display: flex;
    }
    .result {
      padding: 0px 18px 18px 18px;
    }
    .result button{
      width: 100%;
      background-color: #8739f9;
      color: #f2f5f5;
      border: none;
      border-radius: 7px;
      -webkit-box-shadow: -2px 3px 3px -1px rgba(133,133,133,1);
      -moz-box-shadow: -2px 3px 3px -1px rgba(133,133,133,1);
      box-shadow: -2px 3px 3px -1px rgba(133,133,133,1);
    }
    .screen {
      padding: 18px 18px 0 18px;
    }
    #result {
      background-color: #9a9c9c;
      color: #eee;
      padding: 9px;
    }
    .numbers {
      padding: 18px 9px 18px 18px;
    }
    .op {
      padding: 18px 18px 18px 9px;
    }
    #clear {
      width: 35%;
      height: 54px;
      margin-left: 2px;
      background-color:#3f7dbb;
      color: #f1f1f1;
      border:none;
    }
    .op button {
      display: block;
      width: 54px;
      height: 54px;
      padding: 10px 15px;
      margin: 5px 0;
      background-color:#37b9f1;
      color: #f1f1f1;
      border: none;
      border-radius: 7px;
      -webkit-box-shadow: -2px 3px 3px -1px rgba(133,133,133,1);
      -moz-box-shadow: -2px 3px 3px -1px rgba(133,133,133,1);
      box-shadow: -2px 3px 3px -1px rgba(133,133,133,1);
    }
    .numbers div {
      text-align: center;
    }
    .numbers button {
      border: 0px;
      background-color: #f1f1f1;
      transition: all 0.2s;
      -webkit-box-shadow: -2px 3px 3px -1px rgba(133,133,133,1);
      -moz-box-shadow: -2px 3px 3px -1px rgba(133,133,133,1);
      box-shadow: -2px 3px 3px -1px rgba(133,133,133,1);
      border-radius: 7px;
    }
    button {
      margin: 2px 2px;
      padding: 15px 24px;
      font-size: 19px;
    }
    button:hover {
      box-shadow: 0px 0px 6px #37b9f1;
      transition: all 0.2s;
    }
    &-sign {
      width: 100%;
      height: 20px;
      display: flex;
      justify-content: center;
      align-items: center;
    }
    .sign {
      text-decoration: none;
      font-size: 0.8rem;
      color: #3f7dbb;
    }
  }
</style>

<script>
export default {
  name: 'Calculatorcomponent',
  data () {
    return {
      valorCorriente: '',
      numeroAnterior: null,
      operador: null,
      operadorClickeado: false
    }
  },
  methods: {
    limpiar () {
      this.valorCorriente = ''
    },
    enviarNumero (numero) {
      if (this.operadorClickeado) {
        this.valorCorriente = ''
        this.operadorClickeado = false
      }
      this.valorCorriente = `${this.valorCorriente}${numero}`
    },
    setearValor () {
      this.numeroAnterior = this.valorCorriente
      this.operadorClickeado = true
    },
    dividir () {
      this.operador = (num1, num2) => num1 / num2
      this.setearValor()
    },
    multiplicar () {
      this.operador = (num1, num2) => num1 * num2
      this.setearValor()
    },
    sumar () {
      this.operador = (num1, num2) => num1 + num2
      this.setearValor()
    },
    restar () {
      this.operador = (num1, num2) => num1 - num2
      this.setearValor()
    },
    resultado () {
      this.valorCorriente = `${this.operador(
        parseFloat(this.numeroAnterior),
        parseFloat(this.valorCorriente)
      )}`
      this.numeroAnterior = null
    }
  }
}
</script>
