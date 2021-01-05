<template>
  <button :style="background">
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
    background: String
  }
}
</script>

<style scoped>
  button{
    border: none;
    background: #373737;
    cursor: pointer;
    outline-style: none;
    display: flex;
    justify-content: center;
    align-items: center;
  }
  button:active{
    background:#006A6A;
  }
  span{
    color: #EFEFEF;
    font-size: 1.5rem;
  }
  .number{
    font-weight: bold;
  }

</style>
