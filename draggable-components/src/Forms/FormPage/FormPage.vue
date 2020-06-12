<template>
    <div class="form-inputs">
        <cardInputForm :updateEdited='updateEdited'
                    :addTask='addTask'
                    :tempValue='tempValue'
                    :text='text'
                    :onEdit='onEdit'/>
        <boardInputForm :boardName='boardName'
                    :addNewBoard='addNewBoard'/>
    </div>
</template>

<script>
import CardInputForm from '../components/CardInputForm'
import BoardInputForm from '../components/BoardInputForm'

export default {
  props: [
    'updateEdited',
    'addTask',
    'tempValue',
    'text',
    'boardName',
    'addNewBoard',
    'onEdit'
  ],
  components: {
    CardInputForm,
    BoardInputForm
  }
}
</script>
