<template>
  <div class="board">
    <div
      v-for="(cell, index) in board"
      :key="index"
      class="cell"
      @click="makeMove(index)"
    >
      {{ cell }}
    </div>
  </div>
</template>

<script>
export default {
  props: ['board', 'makeMove'],
};
</script>

<style scoped>
.board {
  display: grid;
  grid-template-columns: repeat(3, 100px);
  grid-gap: 5px;
}

.cell {
  width: 100px;
  height: 100px;
  border: 1px solid #ccc;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 24px;
  cursor: pointer;
}
</style>
