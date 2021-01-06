<template>
  <button :value="value" :style="style" @click="click">
    <span class="material-icons">
      {{ icon }} 
    </span>
    <span class="number">
      {{ number }}
    </span>
    <span class="letter">
      {{ letter }}
    </span>
  </button>
</template>

<script>
export default {
  name: 'Key',
  props: {
    icon: String,
    number: Number,
    letter: String,
    value: String,
    click: Function
  },
  data () {
    return {
      style: ''
    }
  },
  methods: {
    upgradeBackground () {
      if (this.icon || this.letter || this.icon === 'backspace') {
        this.style = 'background: var(--color-darkgrey);'
      } 
      if (this.icon === 'drag_handle') {
        this.style = 'background: var(--color-orange);'
      } 
      if (this.number) {
        this.style = 'background: var(--color-grey);'
      }
      if (this.letter === '.' || this.letter === '+/-' || this.number === 0){
        this.style = 'background: var(--color-grey);'
      }
    }
  },
  created () {
    this.upgradeBackground ();
  }
}
</script>

<style>
  button{
    border: none;
    cursor: pointer;
    outline-style: none;
    display: flex;
    justify-content: center;
    align-items: center;
    transition: all 100ms;
  }
  button:active {
    transform: translate(1px, 1px);
  }
  span{
    color: var(--color-white);
    font-size: 1.5rem;
  }
  .number{
    font-weight: bold;
  }

</style>
