<template>
  <div class="home">
    <h1>Home</h1>
    <!-- type in the field to update the value of refs -->
    <input type="text" v-model="search">
    <p>search term - {{ search }}</p>
    <!-- Output name -->
    <!-- <p>{{ name }}</p> -->
    <div v-for="name in matchingNames" :key="name">{{ name }}</div>
   </div>
</template>

<script>
// Composition API refs are useful to make values reactive
// the pattern of importing only the features we need
import { computed, ref } from 'vue'
// Component object
export default {
  name: 'Home',
  setup() {
    // const name = computed(() => {
    //   return 'shaun'
    // })
//  return { name }
// Using with refs
const search = ref('')

const names = ref(['mario','yoshi', 'luigi', 'toad', 'bowser', 'koopa', 'peach'])

// Return a computed value based on the updated search
const matchingNames = computed(() => {
  // return computed value (of the ref())
  // Use .includes on a string
  // if it returns false , the search term is removed for the array, it filteres it out
  return names.value.filter((name) => name.includes(search.value))
}) 

return { names, search, matchingNames }
   } 
}
</script>
