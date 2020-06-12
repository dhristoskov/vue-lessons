<template>
    <div class="tasks-input">
          <input v-if="onEdit" type="text" v-model="newTempValue.text" @keyup.enter='updateEdited(newTempValue)'>
          <input v-else type="text" placeholder="New Entry" v-model="text" @keyup.enter='addTask(text)' />
          <input v-if="onEdit" type='submit' value='edit' @click="updateEdited(newTempValue)"/>
          <input v-else type='submit' value='submit' @click="addTask(text)"/>
    </div>
</template>

<script>
export default {
  props: [
    'updateEdited',
    'addTask',
    'tempValue',
    'onEdit'
  ],
  data () {
    return {
      text: '',
      newTempValue: this.tempValue
    }
  }

}
</script>
