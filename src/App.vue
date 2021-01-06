<template>
  <div id="app">
    <Calc />
  </div>
</template>

<script>
import Calc from './components/Calc'
export default {
  name: 'App',
  components: {
    Calc
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
  
</style>
