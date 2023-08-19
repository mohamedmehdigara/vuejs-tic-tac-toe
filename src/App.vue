<template>
  <div id="app">
    <h1>Tic Tac Toe</h1>
    <TicTacToeBoard :board="board" :makeMove="makeMove" />
    <div v-if="winner">
      <p>{{ winner }} wins!</p>
      <button @click="resetGame">Play Again</button>
    </div>
  </div>
</template>

<script>
import TicTacToeBoard from './components/TicTacToeBoard.vue';

export default {
  components: {
    TicTacToeBoard,
  },
  data() {
    return {
      currentPlayer: 'X',
      board: Array(9).fill(''),
      winner: null,
    };
  },
  methods: {
    makeMove(index) {
      if (!this.board[index] && !this.winner) {
        this.board[index] = this.currentPlayer;
        this.checkWinner();
        this.currentPlayer = this.currentPlayer === 'X' ? 'O' : 'X';
      }
    },
    checkWinner() {
      // ... (rest of your checkWinner logic)
    },
    resetGame() {
      this.currentPlayer = 'X';
      this.board = Array(9).fill('');
      this.winner = null;
    },
  },
};
</script>

<style>
/* Your styles here */
</style>
