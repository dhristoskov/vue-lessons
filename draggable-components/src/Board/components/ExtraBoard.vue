<template>
    <div class="board"
        :id='board.id'
        @dragover.prevent
        @drop.prevent='drop'>
        {{board.name}}
        <slot />
    </div>
</template>

<script>
export default {
  props: ['board'],
  methods: {
    drop: e => {
      const cardId = e.dataTransfer.getData('cardId')
      const card = document.getElementById(cardId)
      card.style.display = 'block'
      e.target.appendChild(card)
    }
  }
}
</script>

<style lang="scss" scoped>
  .board {
      display: flex;
      flex-direction: column;
      width: 100%;
      max-width: 300px;
      min-height: 200px;
      padding: 15px;
      background-color: blue;
      margin: 10px;
  }
</style>
