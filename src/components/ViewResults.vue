<template>
  <p>ReactionTime: {{ score }} ms</p>
  <p class="rank">{{this.rank}}</p>
</template>

<script>
export default {
  props: ["score"],
  data() {
    return {
      rank: null,
    };
  },
  mounted() {
    if (this.score < 250) {
      this.rank = 'Ninja Fingers';
    } else if (this.score > 250 && this.score < 600) {
      this.rank = 'Rapid Reflexes'
    } else {
      this.rank = "Snail's Pace"
    }
  }
};
</script>

<style>
.rank{
  font-weight: bold;
  font-size: 1.4rem;
  color: rgb(16, 156, 110);
}
</style>
