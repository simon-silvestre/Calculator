<template>
  <div id="app">
    <div class="calculator">
      <div class="resultContainer">
        <p class="result">{{ result || 0 }}</p>
      </div>
      <div class="keyboard">
        <bouton number="7" @click="action(7)"/>
        <bouton number="8" @click="action(7)"/>
        <bouton number="9" @click="action(7)"/>
        <bouton number="DEL" class="del"/>
        <bouton number="4"/>
        <bouton number="5"/>
        <bouton number="6"/>
        <bouton number="+"/>
        <bouton number="1"/>
        <bouton number="2"/>
        <bouton number="3"/>
        <bouton number="-"/>
        <bouton number="."/>
        <bouton number="0"/>
        <bouton number="/"/>
        <bouton number="*"/>
        <bouton number="RESET" class="reset bigButton"/>
        <bouton number="=" class="equal bigButton"/>
      </div>
    </div>
  </div>
</template>

<script>
import bouton from './components/button.vue'

export default {
  name: 'App',
  components: {
    bouton
  },
  data() {
    return {
      result: '',
      operateur: '',
      previousResultValue: ''
    }
  }
}
</script>

<style lang="scss">
  * {
    padding: 0;
    margin: 0;
    box-sizing: border-box;;
  }
  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    background: #3b4764;
    width: 100vw;
    height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
  }
  .calculator {
    width: 500px;
    height: 600px;
    position: relative;

    .resultContainer, .keyboard {
      position: absolute;
      display: flex;
      align-items: center;
      width: 100%;
      border-radius: 8px;
    }
    .resultContainer {
      height: 15%;
      background: #182032;
      top: 0;
      justify-content: flex-end;

      .result {
        color: #fff;
        font-size: 40px;
        font-weight: bold;
        margin-right: 20px;
      }
    }
    .keyboard {
      height: 80%;
      background: #242e44;
      bottom: 0;
      justify-content: space-between;
      flex-wrap: wrap;
      padding: 20px 30px;

      .del, .bigButton {
        p {
          color: #fcfcff;
          font-size: 20px;
        }
      }
      
      .del, .reset {
        .numberContainer {
          background: #657199;
        }
        .ombre {
          background: #424d74;
        }
      }

      .bigButton {
        width: 210px;
      }

      .equal {
        .numberContainer {
          background: #d14030;
        }
        .ombre {
          background: #94261b;
        }
      }

    }
  }

  @media screen and (max-width: 530px) {
    .calculator {
      width: 300px;
      height: 450px;
      position: relative;

      .resultContainer .result {
        font-size: 30px;
      }

      .keyboard .del, .keyboard .bigButton {
        p {
          font-size: 12px;
        }
      }
      .keyboard .bigButton {
        width: 115px;
      }
    }
  }
</style>
