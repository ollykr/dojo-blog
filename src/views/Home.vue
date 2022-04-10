<template>
  <div class="home">
    <h1>Home</h1>
    <h2>Refs</h2>
    <p>{{ ninjaOne.name }} - {{ ninjaOne.age }}</p>
    <button @click="updateNinjaOne">Update ninja one</button>
    <h2>Reactive</h2>
    <p>{{ ninjaTwo.name }} - {{ ninjaTwo.age }} - {{ nameTwo }}</p>
    <button @click="updateNinjaTwo">Update ninja two</button>
   </div>
</template>

<script>
// Composition API refs are useful to make values reactive
import { ref, reactive } from 'vue'
// Component object
export default {
  name: 'Home',
  setup() {
    // we can use an object as a value of refs
      const ninjaOne = ref({ name: 'mario', age: 30})

// Use reactive , not ref - note: refs are better
const ninjaTwo = reactive({ name: 'luigi', age: 35})
// We can't use primitive values inside reactive
// refs - we can
const nameOne = ref('mario');
// reactive - we can't as 'luigi' is a primitive value
// we can't update it
const nameTwo = reactive('luigi')

const updateNinjaOne = () => {
        ninjaOne.value.age = 40;
      }
      // To update reactive
      const updateNinjaTwo = () => {
    
    // No need to use .value with reactive
    // We access the property directly on it
    ninjaTwo.age = 45
    
    }
      return { ninjaOne, updateNinjaOne, ninjaTwo, updateNinjaTwo, nameTwo}
   } 
}
</script>
