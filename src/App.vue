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
          <Key letter="C"/>
          <Key :icon="keysIcon[0]"/>
          <Key letter="%"/>
          <Key letter="/"/>
          <Key :number="7"/>
          <Key :number="8"/>
          <Key :number="9"/>
          <Key :icon="keysIcon[1]"/>
          <Key :number="4"/>
          <Key :number="5"/>
          <Key :number="6"/>
          <Key :icon="keysIcon[2]"/>
          <Key :number="1"/>
          <Key :number="2"/>
          <Key :number="3"/>
          <Key :icon="keysIcon[3]"/>
          <Key letter="+/-"/>
          <Key :number="0"/>
          <Key letter="."/>
          <Key :icon="keysIcon[4]"/>
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
    font-family: Arial, Helvetica, sans-serif;
    width: 100vw;
    height: 100vh;
    margin: 0;
    padding: 0;
    background: #EFEFEF;
    display: flex;
    justify-content: center;
    align-items: center;
  }
  .app-container{
    max-width: 300px;
    max-height: 500px;
    height: 100%;
    width: 100%;
    border: 3px solid #006A6A;
    box-shadow: 2px 2px 5px rgba(0,0,0,.6);
    display: grid;
    grid-template-rows: 60px 1fr;
  }
  .header-container{
    background: #006A6A;
    display: flex;
    justify-content: center;
    align-items: center;
  }
  .main-container{
    background: #000;
    display: grid;
    grid-template-rows: 30% 1fr;
  }
  .result-content{
    color: #EFEFEF;
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
