<template>
  <div class="home">
    <h1>Home</h1>
    <!-- type in the field to update the value of refs -->
    <input type="text" v-model="search">
    <p>search term - {{ search }}</p>
    <!-- Output name -->
    <!-- <p>{{ name }}</p> -->
    <div v-for="name in matchingNames" :key="name">{{ name }}</div>
    <button @click="handleClick">stop watching</button>
   </div>
</template>

<script>
// Composition API refs are useful to make values reactive
// the pattern of importing only the features we need
import { computed, ref, watch, watchEffect } from 'vue'
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
// watch for search updates and fire some code based on the changes
// watch(search, () => {
// console.log('watch function ran')
// })
// How to stop watching
const stopWatch = watch(search, () => {
console.log('watch function ran')
})

// runs initially when a component ran first (before typing anything), or with 'search.value' watches typed values
// Used more often than just watch() as we need often to get a data from a datalist, perhaps that rellies on resource id, if the id changes we need to re-run the resource
// watchEffect(()=> {
//   console.log('watchEffect function ran', search.value)
// })

// How to stop watchEffect
const stopEffect = watchEffect(()=> {
  console.log('watchEffect function ran', search.value)
})
// Return a computed value based on the updated search
const matchingNames = computed(() => {
  // return computed value (of the ref())
  // Use .includes on a string
  // if it returns false , the search term is removed for the array, it filteres it out
  return names.value.filter((name) => name.includes(search.value))
}) 
const handleClick = (()=> {
// Invoke
stopWatch()
stopEffect()
})
return { names, search, matchingNames, handleClick }
   } 
}
</script>
