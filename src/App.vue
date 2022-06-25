<template>
  <h1>Ninja Reaction Timer</h1>
  <button @click="start" :disabled="isPlaying" class="btn">Play</button>
  <TodoItem v-if="isPlaying" :delay="delay" @end="endGame"/>
  <!-- <p v-if="showResults">Reaction Time: {{score}} ms</p> -->
  <ViewResults v-if="showResults" :score = "this.score"/>
</template>

<script>
import TodoItem from './components/TodoItem.vue';
import ViewResults from './components/ViewResults.vue';

export default {
  name: 'App',
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResults: false,
    }
  },
  methods: {
    start() {
      this.delay = 2000 + Math.random() * 5000;
      this.isPlaying = true;
      this.showResults = false;
    },
    endGame(reactionTime) {
      this.score = reactionTime;
      this.isPlaying = false;
      this.showResults = true;
    }
  },
  components: { TodoItem , ViewResults},
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #444;
  margin-top: 60px;
}

.btn{
  background: rgb(48, 155, 119);
  color: aliceblue;
  border: none;
  font-size: 16px;
  height: 30px;
  width: 80px;
  border-radius: 3px;
}
button[disabled]{
  opacity: 0.2;
  cursor: not-allowed;
}
</style>
