<template>
  <div class="container column">
    <app-input @add-new-block="addNewBlock"></app-input>
    <app-view></app-view>
  </div>
  <div class="container">
    <app-comments>
    </app-comments>
    <app-loader>
    </app-loader>
  </div>
</template>

<script>
import AppLoader from './components/AppLoader'
import AppInput from './components/AppInput'
import AppView from './components/AppView'
import AppComments from './components/AppComments'

export default {
  data () {
    return {
      blocks: [],
      comments: [],
      loading: false
    }
  },
  methods: {
    addNewBlock (block) {
      console.log('AddNewBlock')
      this.blocks.push(block)
      console.log('blocks=', this.blocks)
    }
  },
  components: { AppLoader, AppInput, AppView, AppComments }

}
</script>

<style>
.avatar {
  display: flex;
  justify-content: center;
}

.avatar img {
  width: 150px;
  height: auto;
  border-radius: 50%;
}
</style>
