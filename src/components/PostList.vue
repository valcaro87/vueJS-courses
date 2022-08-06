<template>
  <div>
    <h2>list of all posts</h2>
    <button @click="getPosts"> Load all posts </button>
    <div v-if="errorMessage"> {{ errorMessage }}</div>
    <div class="allposts">
      <ul v-for="(post) in allPost" :key="post.id">
        <div class="eachpost">
          <h2> {{ post.title }} </h2>
          <p>{{ post.body }} - {{ post.views }} </p>
        </div>
      </ul>
    </div>

    <hr />
    <div class="allphotos">
      <h2>Photos</h2>
      <ul v-for="(photo) in allPhotos" :key="photo.id">
        <div class="eachphoto">
          <h2> {{ photo.title }} </h2>
          <p>{{ photo.url }} </p>
          <img :src="photo.thumbnailUrl" :alt="photo.title">
        </div>
      </ul>
    </div>

  </div>
</template>
<script>
import axios from 'axios'
export default {
  name: 'PostList',
  data() {
    return {
      allPost: [],
      allPhotos: [],
      errorMessage: ''
    }
  },
  methods: {
    getPosts() {
      let accessToken = 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VyX2lkIjoxNX0.NZ7xF2BHWLxH5M8QB9lR7lvj6nPZTcYtOwVtOPVtuHU'
      axios
        // .get('http://localhost:3000/api/v1/posts', {
        .get('http://localhost:3000/api/v1/posts', {
          // params: {
          //   _limit: 10
          // }
          headers: {
            Authorization: `Bearer ${accessToken}`,
          },
        })
        .then((response) => {
          // console.log("🚀 ~ .then ~ response.data", response.data)
          this.allPost = response.data
        }).catch((error) => {
          this.errorMessage = `Error in retrieving data: ${error}`
          // console.log(error)
        })
    }
  },
  mounted() {
    axios
      .get('https://jsonplaceholder.typicode.com/photos', {
        params: {
          _limit: 5
        }
      })
      .then((response) => {
        this.allPhotos = response.data
      }).catch((error) => {
        this.errorMessage = `Error in retrieving photos: ${error}`
      })
  },
}
</script>
<style scoped>
.allposts ul {
  list-style-type: square;
}

.allposts {
  margin: 0px auto;
  width: 40%;
}

.eachpost {
  border-top: 1px solid black;
}
</style>