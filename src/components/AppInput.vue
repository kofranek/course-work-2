<template>
  <form class="card card-w30" @submit.prevent="submit">
    <div class="form-control">
      <label for="type">Block type</label>
      <select id="type" v-model="value">
        <option value="title">Title</option>
        <option value="subtitle">Subtitle</option>
        <option value="avatar">Avatar</option>
        <option value="text">Text</option>
      </select>
    </div>

    <div class="form-control">
      <label for="value">Value</label>
      <textarea v-model="content" id="value" rows="3"></textarea>
    </div>

    <button class="btn primary" :disabled="!canSubmit">Add block</button>
  </form>
</template>

<script>
export default {
  name: 'AppInput',
  emits: ['add-new-block'],
  data () {
    return {
      value: 'title',
      content: ''
    }
  },
  methods: {
    submit () {
      this.$emit('add-new-block', {
        type: this.value,
        content: this.content,
        id: Date.now()
      })
      this.content = ''
      this.value = 'title'
    }
  },
  computed: {
    canSubmit () {
      return this.content.length > 3
    }
  }
}
</script>

<style scoped>

</style>
