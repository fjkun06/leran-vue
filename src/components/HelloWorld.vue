<script setup lang="ts">
import { onMounted, ref } from "vue"

defineProps<{
  msg: string
}>()

const name = ref("Vue.js")

function greet(e: Event) {
  alert(`Hello ${name.value}`)
  const button = e.target as HTMLButtonElement

  if (e) {
    alert(button.tagName);
  }
}


//form input bindings
const text = ref('')
const checked = ref(true)

onMounted(() => {
  console.log(`the component is now mounted.`)
})

</script>

<template>
  <div class="greetings">
    <h1 class="green">{{ msg }}</h1>
    <h3>
      You’ve successfully created a project with
      <a href="https://vitejs.dev/" target="_blank" rel="noopener">Vite</a> +
      <a href="https://vuejs.org/" target="_blank" rel="noopener">Vue 3</a>. What's next?
    </h3>
    <button @click="greet">Greet</button>
    <br/>
    <span >My bro says : {{ text }}</span>
    <textarea v-model="text"></textarea>
    <br/>

    <input v-model="text" placeholder="type sth" />
    <br/>

    <input v-model="checked" type="checkbox"  id="checkbox" />
    <label for="checkbox"> {{ checked }} </label>
    <br/>
    <span v-if="checked">its true </span>
    <span v-else>It is not true </span>
  </div>
</template>

<style scoped>
h1 {
  font-weight: 500;
  font-size: 2.6rem;
  position: relative;
  top: -10px;
}

h3 {
  font-size: 1.2rem;
}

.greetings h1,
.greetings h3 {
  text-align: center;
}

@media (min-width: 1024px) {
  .greetings h1,
  .greetings h3 {
    text-align: left;
  }
}
</style>
