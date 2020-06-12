<template>
    <div class="boards">
      <board id='bord-01'>
       <card draggable="true" v-for="card in cardData"
                  :key="card.id"
                  :card='card'
                  :removeTask='removeTask'
                  :editTask='editTask'/>
      </board>
      <extra-board v-for="board in boards" :key="board.id" :board='board'/>
    </div>
</template>

<script>
import Board from '../components/Board'
import Card from '../../Card/Card'
import ExtraBoard from '../components/ExtraBoard'

export default {
  props: [
    'cardData',
    'removeTask',
    'editTask',
    'boards'
  ],
  components: {
    Board,
    ExtraBoard,
    Card
  }
}
</script>

<style lang="scss" scoped>
  .boards {
    padding: 30px;
    display: flex;
    justify-content: space-between;
    flex-wrap: wrap;
    width: 100%;
    max-width: 1100px;
    margin: auto;
  }
</style>
