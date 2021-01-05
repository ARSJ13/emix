<template>
  <div id="app">
    <div class="app-container">
      <header class="header-container">
        <img src="./assets/logo.png" alt="Logo">
      </header>
      <main class="main-container">
        <section class="result-content">
          <p v-model="result">{{ result | calculation }}</p>
          <h2>{{ result | calculation }}</h2>
        </section>
        <section class="keys-content">
          <Key letter="C" style="background: var(--color-darkgrey)"/>
          <Key :icon="keysIcon[0]" style="background: var(--color-darkgrey)"/>
          <Key letter="%" style="background: var(--color-darkgrey)"/>
          <Key letter="/" style="background: var(--color-darkgrey)"/>
          <Key :number="7" style="background: var(--color-grey)"/>
          <Key :number="8" style="background: var(--color-grey)"/>
          <Key :number="9" style="background: var(--color-grey)"/>
          <Key :icon="keysIcon[1]" style="background: var(--color-darkgrey)"/>
          <Key :number="4" style="background: var(--color-grey)"/>
          <Key :number="5" style="background: var(--color-grey)"/>
          <Key :number="6" style="background: var(--color-grey)"/>
          <Key :icon="keysIcon[2]" style="background: var(--color-darkgrey)"/>
          <Key :number="1" style="background: var(--color-grey)"/>
          <Key :number="2" style="background: var(--color-grey)"/>
          <Key :number="3" style="background: var(--color-grey)"/>
          <Key :icon="keysIcon[3]" style="background: var(--color-darkgrey)"/>
          <Key letter="+/-" style="background: var(--color-grey)"/>
          <Key :number="0" style="background: var(--color-grey)"/>
          <Key letter="." style="background: var(--color-grey)"/>
          <Key :icon="keysIcon[4]" style="background: var(--color-orange)"/>
        </section>
      </main>
    </div>
  </div>
</template>

<script>
import Key from './components/Key'
export default {
  name: 'App',
  components: {
    Key
  },
  data () {
    return {
      result: "10043350",
      keysIcon: ['backspace', 'close',  'remove', 'add', 'drag_handle']
    }
  },
  filters: {
    calculation(event) {
      return event.toLocaleString("pt-BR", {style: "decimal"})
    }
  }
}
</script>

<style>
  h1, h2, h3, p{
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }
    
  #app{
    --color-white: #efefef;
    --color-back: #000;
    --color-green: #006A6A;
    --color-grey: #373737;
    --color-darkgrey: #262626;
    --color-orange: #DF7F00;

    font-family: Arial, Helvetica, sans-serif;
    width: 100vw;
    height: 100vh;
    margin: 0;
    padding: 0;
    background: var(--color-white);
    display: flex;
    justify-content: center;
    align-items: center;
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
    grid-template-rows: 1fr 1fr 1fr 1fr 1fr;
    grid-template-columns: 1fr 1fr 1fr 1fr;
    gap: 0.2rem;
  }
</style>
