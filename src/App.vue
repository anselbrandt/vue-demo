<template>
  <div>counter: {{ counter }}</div>
  <div>
    <span v-bind:title="message"> hover to show dynamically bound title </span>
  </div>
  <div>
    <p>{{ message2 }}</p>
    <button v-on:click="reverseMessage">Reverse Message</button>
  </div>
  <div id="two-way-binding">
    <p>{{ message3 }}</p>
    <input v-model="message3" />
  </div>
  <div>
    <span v-if="seen">Now you see me</span>
  </div>
  <div>
    <ol>
      <li v-for="(todo, index) in todos" :key="index">
        {{ todo.text }}
      </li>
    </ol>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "App",
  components: {},
  data() {
    return {
      counter: 0,
      message: "You loaded this page on " + new Date().toLocaleString(),
      message2: "reversible",
      message3: "two-way binding",
      seen: true,
      todos: [
        { text: "Learn JavaScript" },
        { text: "Learn Vue" },
        { text: "Build something awesome" },
      ],
    };
  },
  mounted() {
    setInterval(() => {
      this.counter++;
    }, 1000);
  },
  methods: {
    reverseMessage() {
      this.message2 = this.message2.split("").reverse().join("");
    },
  },
});
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
