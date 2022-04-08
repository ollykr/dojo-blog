<template>
  <div class="home">
    Home
    <p ref="p" >My name is {{ name }} and my age is {{ age }}</p>
    <!-- Click the button to fire up handleClick function -->
    <button @click="handleClick">click me</button>
  </div>
</template>

<script>
// in composition API we import refs from Vue, it is different in options API
// Composition API is rarelu used for manipulating DOM content, it can be done differently. But composition API refs are useful to make values reactive
import { ref } from 'vue'
// Component object
export default {
  name: 'Home',
  // Composition API
  // Order of running : setup, created, mounted
  setup() {
  console.log(this)
//  p as paragraph
// below is referenced to paragraph tag <p ref="p" >My name is {{ name }} and my age is {{ age }}</p>
// Value property is null
// We have not returned it
  const p = ref(null) 
  // We can run inside any kind of JS
  // we can grab data from somewhere or create a computed property

  // vars
  // not reactive values
  let name = 'mario'
  let age = 30

// we can also create functions
const handleClick = () => {
  // log out p i.e paragraph tag
  // in console we see a ref object
  // _value: p - it is an actual DOM reference
  // also output a p value, a template element <p>My name is mario and my age is 30</p>
console.log(p, p.value);
// Add CSS class "test" to that paragraph
p.value.classList.add('test');
// Change text content on "click me"
p.value.textContent = 'hello, ninjas';
} 
//  p for refs
  return { name, age, handleClick, p }
   } 
  
}
</script>
