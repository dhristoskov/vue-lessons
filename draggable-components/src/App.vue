<template>
  <div class="main">
      <main-header />
      <div class="settings">
        <div class="tasks-input">
          <input v-if="onEdit" type="text" v-model="tempValue.text" @keyup.enter='updateEdited'>
          <input v-else type="text" placeholder="New Entry"  v-model="text" @keyup.enter='addTask' />
          <input v-if="onEdit" type='submit' value='edit' @click="updateEdited"/>
          <input v-else type='submit' value='submit' @click="addTask"/>
        </div>
        <div>
          <input type="text" placeholder="Create a board" v-model="boardName" @keyup.enter='addNewBoard'>
          <input type='submit' value='submit'  @click="addNewBoard"/>
        </div>
      </div>
      <board :cardData='cardData'
             :removeTask='removeTask'
             :editTask='editTask'
             :boards='boards'/>
  </div>
</template>

<script>
import { cardData } from './data'
import Board from './Board/Page/BoardPage'
import MainHeader from './Header/MainHeader'

export default {
  data () {
    return {
      boards: [],
      boardName: '',
      onEdit: false,
      tempValue: null,
      cardData,
      text: ''
    }
  },
  components: {
    Board,
    MainHeader
  },
  methods: {
    addTask (text) {
      this.cardData.push({ id: Date.now(), text: this.text })
      this.text = ''
    },
    removeTask (id) {
      this.cardData = this.cardData.filter(e => e.id !== id)
    },
    editTask (id) {
      const item = this.cardData.find(e => e.id === id)
      this.tempValue = item
      this.toggleEdit()
    },
    toggleEdit () {
      this.btnLebel = this.btnLebel === 'submit' ? 'edit' : 'submit'
      this.onEdit = !this.onEdit
    },
    updateEdited () {
      const edited = this.cardData.find(e => e.id === this.tempValue.id)
      edited.text = this.tempValue.text
      this.onEdit = false
    },
    addNewBoard () {
      if (this.boardName !== '') {
        this.boards.push({ id: Date.now(), name: this.boardName })
        this.boardName = ''
      }
    }
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
</style>
