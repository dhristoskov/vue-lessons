<template>
    <div class="card"
    :id='card.id'
    :draggable="draggable"
    @dragstart="dragstart"
    @dragover.stop>
        {{card.text}}
    </div>
</template>

<script>
export default {
  props: ['draggable', 'card'],
  methods: {
    dragstart: e => {
      e.dataTransfer.setData('cardId', e.target.id)
      setTimeout(() => {
        e.target.style.display = 'none'
      }, 0)
    }
  }
}
</script>

<style lang="scss" scoped>
    .card {
        padding: 15px;
        border: 1px solid black;
        margin-bottom: 10px;
        cursor: pointer;
        background-color: cadetblue;
    }
</style>
