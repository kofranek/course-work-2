<template>
  <div class="container column">
    <app-input @add-new-block="addNewBlock"/>
    <app-view :blocks="blocks"/>
  </div>
  <div class="container">
    <app-comments/>
  </div>
</template>

<script>
import AppInput from './components/AppInput'
import AppView from './components/AppView'
import AppComments from './components/AppComments'

export default {
  data () {
    return {
      blocks: []
    }
  },
  methods: {
    addNewBlock (block) {
      this.blocks.push(block)
    }
  },
  components: { AppInput, AppView, AppComments }

}
</script>

<style>

</style>
