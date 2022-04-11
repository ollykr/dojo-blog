<template>
  <div class="post-list">
<!-- cycle through post lists -->
<!-- post.id - as id property in each list  -->
<div v-for="post in posts" :key="post.id">
    <!-- <h3>{{ post.title }}</h3> -->
<!-- instead -->
<SinglePost :post="post" />
</div>
  </div>
</template>

<script>
import SinglePost from './SinglePost.vue'
export default {
// accept posts as a prop
props: ['posts'],
components: { SinglePost },
setup(props) {
    // access the posts directly
    console.log(props.posts)
}
}
</script>

<style>

</style>