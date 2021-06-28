<template>
  <div class="button">
    <div class="numberContainer" @click="action(number)">
      <p>{{ number }}</p>
    </div>
    <span class="ombre"></span>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    number: String
  },
  methods: {
    action(value) {
      /* inscricre les valeurs */
        if(!isNaN(value) || value === '.' && !this.$parent.result.includes('.')) {
        this.$parent.result += value + ''
      }
      
      /* reinitialiser  */
      if(value === 'RESET') {
        this.$parent.result = ''
      }

      /* effacer */
      if(value === 'DEL') {
        this.$parent.result = this.$parent.result.substring(0, this.$parent.result.length-1)
      }

      /* addition */ 
      if(value === '+' || value === '-' || value === '/' || value === '*') {
        this.$parent.operateur = value 
        this.$parent.previousResultValue = this.$parent.result
        this.$parent.result = ''
      }

      /* resultat */
      if(value === '=') {
        
        this.$parent.result = eval(this.$parent.previousResultValue + this.$parent.operateur + this.$parent.result)

        this.$parent.previousResultValue = ''
        this.$parent.operateur = ''
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.button {
  width: 95px;
  height: 60px;
  position: relative;
  cursor: pointer;

  .numberContainer {
    display: flex;
    justify-content: center;
    align-items: center;
    position: relative;
    background: #e9e3db;
    border-radius: 8px;
    z-index: 1;
    width: 100%;
    height: 55px;
    transition: all .1s;

    &:active {
      height: 60px;
    }
  }
  p {
    font-size: 35px;
    font-weight: bold;
    color: #464a59;
  }
  .ombre {
    position: absolute;
    width: 100%;
    height: 30px;
    background: #b2a296;
    border-radius: 8px;
    bottom: 0;
  }
}
</style>
