<template>
    <div>
        <input type="text" placeholder="Create a board"
        v-model="boardName" @keyup.enter='addNewBoard'>
        <input type='submit' value='submit'  @click="addNewBoard"/>
    </div>
</template>

<script>
export default {
  props: [
    'boardName',
    'addNewBoard'
  ]
}
</script>
