<template>
  <div class="home">
    Home
    <p>My name is {{ name }} and my age is {{ age }}</p>
    <!-- Click the button to fire up handleClick function -->
    <button @click="handleClick">click me</button>
  </div>
</template>

<script>
// Component object
export default {
  name: 'Home',
  // Composition API
  // Order of running : setup, created, mounted
  setup() {
  console.log('setup')
  // We can run inside any kind of JS
  // we can grab data from somewhere or create a computed property

  // vars
  // not reactive values
  let name = 'mario'
  let age = 30

// we can also create functions
const handleClick = () => {
console.log('you clicked me')
} 
  // to use the above vars in a template at the top of our component
  //  return { name: name, age: age }
  // OR
  // return values including a function as the third parameter
  return { name, age, handleClick }
   } 
  //  data() is different from the above as age: 40 is reactive, vars are not
  //  data() {
  //    return {
  // reactive value reflected in a component's template right away
  //      age: 40
  //    }
  //  }
  // created hook
  // created() {
  // console.log('created')
  // },
  // mounted hook
  // mounted() {
  // console.log('mounted')
  // }
}
</script>
