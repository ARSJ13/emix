<template>
  <button :style="style">
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
    style: String
  }
}
</script>

<style scoped>
  button{
    border: none;
    cursor: pointer;
    outline-style: none;
    display: flex;
    justify-content: center;
    align-items: center;
  }
  button:active{
    background: var(--color-green); 
  }
  span{
    color: var(--color-white);
    font-size: 1.5rem;
  }
  .number{
    font-weight: bold;
  }

</style>
