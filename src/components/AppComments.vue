<template>
  <p v-if="showUploadButton">
    <button class="btn primary" @click="uploadComments">Upload comments</button>
  </p>
  <app-loader v-else-if="loading"/>
  <div v-else class="card">
    <h2>Comments</h2>
    <ul class="list" v-for="comment in comments" :key="comment.id">
      <li class="list-item">
        <div>
          <p><strong>{{ comment.email }}</strong></p>
          <small>{{ comment.body }}</small>
        </div>
      </li>
    </ul>

  </div>

</template>

<script>
import AppLoader from '@/components/AppLoader'

export default {
  name: 'AppComments',
  components: { AppLoader },
  data () {
    return {
      comments: [],
      loading: false
    }
  },
  methods: {
    async uploadComments () {
      const url = 'https://jsonplaceholder.typicode.com/comments?_limit=42'
      this.loading = true
      const response = await fetch(url, {
        method: 'GET',
        headers: {
          'Content-Type': 'application/json'
        }
      })
      this.comments = await response.json()
      setTimeout(() => {
        this.loading = false
      }, 2000)
    }
  },
  computed: {
    showUploadButton () {
      return this.comments.length === 0
    }
  }
}
</script>

<style scoped>

</style>
