<template>
  <div class="hello-word">
    <h1 class="text-center">Player Score Counter</h1>
    <div class="card">
      <div class="card-body text-center">
        <h2 class="mb-4">Player 1</h2>
        <button @click="increaseScore(playerOne)" type="button" class="btn btn-success">UP</button>
        <span class="player-score">{{ playerOne.score }}</span>
        <button @click="decreaseScore(playerOne)" type="button" class="btn btn-danger">DOWN</button>
        <h2 class="my-4">Player 2</h2>
        <button @click="increaseScore(playerTwo)" type="button" class="btn btn-success">UP</button>
        <span class="player-score">{{ playerTwo.score }}</span>
        <button @click="decreaseScore(playerTwo)" type="button" class="btn btn-danger">DOWN</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Score',
  data() {
    return {
      playerOne: {
        score: 0,
      },
      playerTwo: {
        score: 0,
      },
    };
  },
  methods: {
    increaseScore(player) {
      player.score += 1;
    },
    decreaseScore(player) {
      if (player.score === 0) {
        return;
      }
      player.score -= 1;
    },
  },
};
</script>

<style>
.player-score {
  font-size: 1.3rem;
  margin: 0 1rem;
}
</style>
