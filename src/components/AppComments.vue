<template>
  <p>
    <button v-if="showUploadButton" class="btn primary" @click="uploadComments">Upload comments</button>
  </p>
  <app-loader v-if="loading"/>
  <div v-if="showComments" class="card">
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
      this.loading = false
      this.showComments = false
      console.log(this.comments[1])
      console.log('name=', this.comments[1].name)
      console.log('email=', this.comments[1].email)
      console.log('body=', this.comments[1].body)
    }
  },
  computed: {
    showComments () {
      return this.comments.length > 0
    },
    showUploadButton () {
      return this.comments.length === 0
    }
  }
}
</script>

<style scoped>

</style>
