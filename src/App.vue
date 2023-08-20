<template>
  <div id="app">
    <h1 class="title">Tic Tac Toe</h1>
    <TicTacToeBoard :board="board" :makeMove="makeMove" />
    <div v-if="winner" class="winner">
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
      const winCombos = [
        [0, 1, 2], [3, 4, 5], [6, 7, 8], // Rows
        [0, 3, 6], [1, 4, 7], [2, 5, 8], // Columns
        [0, 4, 8], [2, 4, 6],           // Diagonals
      ];
      
      for (const combo of winCombos) {
        const [a, b, c] = combo;
        if (this.board[a] && this.board[a] === this.board[b] && this.board[a] === this.board[c]) {
          this.winner = this.board[a];
          break;
        }
      }
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
#app {
  font-family: 'Arial', sans-serif;
  text-align: center;
  margin-top: 20px;
}

.title {
  font-size: 24px;
  margin-bottom: 20px;
}

.winner {
  margin-top: 20px;
  font-size: 18px;
}

button {
  margin-top: 10px;
  padding: 5px 10px;
  font-size: 16px;
  cursor: pointer;
  background-color: #007bff;
  color: white;
  border: none;
  border-radius: 5px;
}

button:hover {
  background-color: #0056b3;
}

/* Rest of the styles are in TicTacToeBoard.vue */
</style>
