<template>
    <div class="card"
    :id='card.id'
    :draggable="draggable"
    @dragstart="dragstart"
    @dragover.stop>
        <span @click="removeTask(card.id)">x</span>
        {{card.text}}
        <span @click="editTask(card.id)">e</span>
    </div>
</template>

<script>
export default {
  props: [
    'draggable',
    'card',
    'removeTask',
    'editTask'
  ],
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
