<template>
  <div class="post">
      <h3>{{ post.title }}</h3>
      <p>{{ snippet }}</p>
  </div>
</template>

<script>
import { computed } from 'vue'
export default {
props: ['post'],
setup(props) {
    const snippet = computed(() => {
        // the property to make a snippet from
        // a snippet of first 100 chars of a string
        return props.post.body.substring(0, 100) + '....'
    })
    return { snippet }
}
}
</script>

<style>

</style>