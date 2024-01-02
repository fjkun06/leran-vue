<script setup lang="ts">
import { computed, reactive, ref } from "vue";
interface Props {
  name?: string
  books?:string[]
  age?:number
}
const {name,books,age} = withDefaults(defineProps<Props>(),{name: "frank", age: 22, books: () => ["a", "b", "c"]}) 
const count = ref(0)
console.log(name, age, books);

console.log(count.value) // 0

//reactive
const state = reactive({ text: "hell-o" })
console.log(state.text);

//computed
const author = reactive({
  name: 'John Doe',
  books: [
    'Vue 2 - Advanced Guide',
    'Vue 3 - Basic Guide',
    'Vue 4 - The Mystery'
  ]
})

const hasPublishedBooksMessage = computed(() => author.books.length > 0 ? 'Yes' : 'No')

//clases and styles
const isActive = ref(true)
const hasError = ref(true)
const activeClass = ref('active')
const errorClass = ref('text-danger')

//conditional rendering
const awesome = ref(true)
const show = ref(true)

const toggleVue = () => awesome.value = !awesome.value


//loopx
const items = ref([{ message: 'Foo' }, { message: 'Bar' }])
const myObject = reactive({
  title: 'How to do lists in Vue',
  author: 'Jane Doe',
  publishedAt: '2016-04-10'
})

alert("hello world")
</script>

<template>
  <div class="about" :class="$attrs.class">
    <h1>This is an about page from fjkuno6</h1>
    <p>Count is {{ count }}</p>
    <p>{{ hasPublishedBooksMessage }}</p>
      <button @click="count++">Increment Count</button>
    <button @click="count--">Decrement Count</button>
    <p class="styles" :class="{acive: isActive, 'text-danger':hasError}">Classes and Styles</p>
    <div :class="[{ activeClass: isActive }, errorClass]"></div>
     <div class="cond-rederx">
    <h1 v-if="awesome">Vue is awesome!</h1>
    <h1 v-else>Oh no 😢</h1>
    <h1 v-show="show">Show me</h1>
      <button @click="toggleVue">Toggle Vue with Method</button>
      <button @click="awesome = !awesome">Toggle Vue</button>
      <button @click="show = !show">Toggle Show</button>

  </div>
     <div class="loopx">
      <li v-for="({message}, index) of items" :key="index">
     {{ index }} : {{ message }}
      </li>
      <li v-for="(value,key,i) in myObject" :key="i">
      {{ i }} => {{ key }} : {{ value }}
      </li>
      <span v-for="n in 10" :key="n">
        {{ n }}
      </span>
     </div>
  </div>

 
</template>

<style>
@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    display: flex;
    align-items: center;
    flex-direction: column;
  }
}
</style>
