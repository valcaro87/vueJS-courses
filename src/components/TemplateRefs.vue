<template>
  <div>
    <input type="text" ref="refMeplease">
  </div>

  <div>
    <PostList ref="refPostList" />
  </div>
</template>
<script>
import PostList from './PostList.vue'

export default {
  name: 'TemplateRefs',
  components: {
    PostList,
  },
  mounted() {

    //this.$refs.refMeplease.focus()
    this.$refs.refPostList.focus()
  }
}
</script>
<style scoped>
</style>