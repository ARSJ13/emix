<template>
  <div class="app-container">
      <header class="header-container">
        <img src="@/assets/logo.png" alt="Logo">
      </header>
      <main class="main-container">
        <section class="result-content">
          <p>{{number}}</p>
          <h2>{{resultado}}</h2>
        </section>
        <section class="keys-content">
          <Key letter="C" :click="clear"/>
          <Key :icon="keysIcon[0]" :click="clear"/>
          <Key letter="%" :click="validationOperator"/>
          <Key letter="/" :click="validationOperator"/>
          <Key :number="7" :click="upgradeNumber"/>
          <Key :number="8" :click="upgradeNumber"/>
          <Key :number="9" :click="upgradeNumber"/>
          <Key letter="*" :click="validationOperator"/>
          <Key :number="4" :click="upgradeNumber"/>
          <Key :number="5" :click="upgradeNumber"/>
          <Key :number="6" :click="upgradeNumber"/>
          <Key letter="-" :click="validationOperator"/>
          <Key :number="1" :click="upgradeNumber"/>
          <Key :number="2" :click="upgradeNumber"/>
          <Key :number="3" :click="upgradeNumber"/>
          <Key letter="+" :click="validationOperator"/>
          <Key letter="+/-" :click="upgradeNumber"/>
          <Key :number="0" :click="upgradeNumber"/>
          <Key letter="." :click="upgradeNumber"/>
          <Key :icon="keysIcon[4]" :click="upgradeResult" />
        </section>
      </main>
    </div>
</template>

<script>
import { evaluate } from 'mathjs';
import Key from './Key';
export default {
  name: 'Calc',
  components: {
    Key
  },
  data () {
    return {
      keysIcon: ['backspace', 'close',  'remove', 'add', 'drag_handle'],
      result: false,
      number: '',
      validationNumber: false,
      resultado: ''
    }
  },
  filters: {
    calculation(event) {
      return event.toLocaleString("pt-BR", {style: "decimal"})
    }
  },
  methods: {
    clear() {
      this.result = false;
      this.number = '';
      this.resultado = '';
      this.validationNumber = false;
    },
    validationOperator({target}) {
      if (this.validationNumber) {
        this.number += target.innerText;
        this.validationNumber = false;
        this.result = false;
      }
    },
    upgradeNumber({target}) {
      if (this.result) {
        this.number = target.innerText;
        this.result = false;
        this.validationNumber = true;
      } else {
        this.number += target.innerText;
        this.validationNumber = true;
      }
    },
    async upgradeResult() {
      if (this.number) {
        this.resultado = await evaluate(this.number);
        if (this.resultado === Infinity) {
          this.resultado = 'Não é possível realizar a divisão por 0'
        }
        this.result = true;
      }
    }
  }
}
</script>

<style>
  textarea {
    background: var(--color-back);
    color: var(--color-back);
    border: none;
  }
  p{
    letter-spacing: 0.2rem;
  }
  .app-container{
    max-width: 300px;
    max-height: 500px;
    height: 100%;
    width: 100%;
    border: 3px solid var(--color-green);
    box-shadow: 2px 2px 5px rgba(0,0,0,.6);
    display: grid;
    grid-template-rows: 60px 1fr;
  }
  .header-container{
    background: var(--color-green);
    display: flex;
    justify-content: center;
    align-items: center;
  }
  .main-container{
    background: var(--color-back);
    display: grid;
    grid-template-rows: 30% 1fr;
  }
  .result-content{
    color:var(--color-white);
    text-align: right;
    display: flex;
    flex-direction: column;
    justify-content: space-around;
    padding: 1rem;
  }
  .keys-content{
    display: grid;
    grid-template-rows: repeat(5, 1fr);
    grid-template-columns: repeat(4, 1fr);
    gap: 0.2rem;
  }
</style>