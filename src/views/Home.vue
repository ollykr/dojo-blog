<template>
  <div class="home">
    Home
    <p ref="p" >My name is {{ name }} and my age is {{ age }}</p>
    <!-- Click the button to fire up handleClick function -->
    <button @click="handleClick">click me</button>
    <!-- increase age variable by one on click -->
    <button @click="age++">add 1 to age</button>
    <!-- no need to use name.value as it is in refs below -->
    <!-- Type to change a name value  -->
    <input type="text" v-model="name">
  </div>
</template>

<script>
// Composition API refs are useful to make values reactive
import { ref } from 'vue'
// Component object
export default {
  name: 'Home',
  // Composition API
  // Order of running : setup, created, mounted
  setup() {
// Value property is null
// We have not returned it
  // const p = ref(null) 

// Be default the below vars are not reactive so if we change 'mario' to 'luigi' down below, nothing changes, it won't change paragraph content in a template
// But if we surround them with ref(), there are reactive
// const means ref is constant but values inside refs can change, these are reactive values
const name = ref('mario')
const age = ref(30)

// we can also create functions
const handleClick = () => {
  // Update values of the refs reactively
  name.value = 'luigi'
  age.value = 33
} 
//  p for refs
  return { name, age, handleClick }
   }, 
   
  //Options API the date is reactive by default
  
  data() {
    return {
      score: 5
    }
  }
  
}
</script>
