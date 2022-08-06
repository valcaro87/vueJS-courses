<template>
  <div>
    <form @submit.prevent="createPost" ref="createPostForm">
      <!-- <label for="userId">User ID: </label>
      <input type="text" v-model="formData.userId"> -->

      <label for="title">Title: </label>
      <input type="text" v-model="formData.title">

      <label for="body">Content: </label>
      <textarea cols="30" rows="10" v-model="formData.body" />

      <label for="views">Views: </label>
      <input type="text" v-model="formData.views">

      <button> Create Post</button>
      <div>{{ returnedMessage }}</div>

    </form>
  </div>
</template>
<script>
import axios from 'axios';
export default {
  name: 'CreatePost',
  data() {
    return {
      formData: {
        // userId: '',
        title: '',
        body: '',
        views: 0,
      },
      returnedMessage: ''
    }
  },
  methods: {
    createPost() {
      let accessToken = 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VyX2lkIjoxNX0.NZ7xF2BHWLxH5M8QB9lR7lvj6nPZTcYtOwVtOPVtuHU'
      // let post = this.formData
      axios
        .post('http://localhost:3000/api/v1/posts',
          { post: this.formData }, {
          headers: {
            Authorization: `Bearer ${accessToken}`
          }
        }
        )
        .then((response) => {
          if (response.status === 200) {
            this.$refs.createPostForm.reset()
            this.returnedMessage = 'Post successfully created'
          }
        }).catch((error) => {
          this.returnedMessage = `Error in posting data: ${error}`
        })
    }
    // createPost() {
    //   axios.post('https://jsonplaceholder.typicode.com/posts', this.formData)
    //     .then(response => console.log(response))
    //     .catch(error => console.log(error))
    //   //.then((json) => console.log(json));
    //   // .then((response) => response.json())
    // }
  },
}
</script>
<style scoped>
input[type=text],
select,
textarea {
  width: 20%;
  padding: 12px;
  border: 1px solid #ccc;
  border-radius: 4px;
  box-sizing: border-box;
  margin-top: 6px;
  margin-bottom: 16px;
  resize: vertical;
  display: block;
  margin: 0 auto;
}

input[type=submit] {
  background-color: #04AA6D;
  color: white;
  padding: 12px 20px;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

input[type=submit]:hover {
  background-color: #45a049;
}
</style>