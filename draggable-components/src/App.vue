<template>
  <div class="main">
    <board id='bord-01'>
      <card draggable="true" v-for="card in cardData" :key="card.id" :card='card'/>
    </board>

     <board id='bord-02' />
  </div>
</template>

<script>
import Board from './components/Board/Board'
import Card from './components/Card/Card'
import { cardData } from './data'

export default {
  data () {
    return {
      cardData
    }
  },
  components: {
    Board,
    Card
  }
}
</script>

<style lang="scss">
 * {
    padding: 0;
    margin: 0;
  }

  html {
    box-sizing: border-box;
  }

  *, *::before, *::after {
    box-sizing: inherit;
  }

  .main {
    padding: 30px;
    display: flex;
    justify-content: space-evenly;
    width: 100%;
    max-width: 900px;
  }
</style>
