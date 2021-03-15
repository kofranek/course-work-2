<template>
  <div class="card card-w70">
    <h3 v-if="emptyBlocks">Add the first block to see the result</h3>
    <div v-for="block in blocks" :key="block.id">
      <div v-if="block.type==='title'" id="title">
        <h1>{{ block.content }}</h1>
      </div>
      <div v-else-if="block.type==='subtitle'">
        <h2>{{ block.content }}</h2>
      </div>
      <div v-else-if="block.type==='text'">
        <p>{{ block.content }}</p>
      </div>
      <div v-else-if="block.type==='avatar'">
        <div class="avatar">
          <img :src="block.content">
        </div>
      </div>
    </div>
  </div>
</template>

<script>

export default {
  name: 'AppView',
  props: {
    blocks: Array
  },
  computed: {
    emptyBlocks () {
      return this.blocks.length === 0
    }
  }

}
</script>

<style scoped>
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
