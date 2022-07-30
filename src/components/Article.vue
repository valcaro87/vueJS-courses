<template>
  <div>
    <h1>Article</h1>
    <h2 v-show="isPublished">{{ title }} - {{ likes }}</h2>
    <h2 v-bind="$attrs"> non prop Attributes examples</h2>
  </div>
</template>
<script>


export default {
  name: 'ArticleComp',
  props: {
    title: { type: String, required: true, default: 'ruby on rails 2023' },
    likes: Number,
    isPublished: Boolean,
  },
  inheritAttrs: false // tdisable attr id in parent element
}
</script>

<style scoped>
</style>