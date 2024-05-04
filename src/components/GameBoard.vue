<template>
  <div class="game-board">
    <div v-for="(row, rowIndex) in gameBoard" :key="rowIndex" class="row">
      <div v-for="(cell, colIndex) in row" :key="colIndex" class="cell">
        <input v-model="cell.input" :disabled="cell.completed" class="input-field" @keydown.enter.prevent="checkRow(rowIndex)">
      </div>
    </div>
    <Keyboard :keyboardLayout="keyboardLayout" :activeRowIndex="activeRowIndex" :activeColIndex="activeColIndex" @key-click="appendToActiveRow" @delete-click="deleteLastCharacter" />
  </div>
</template>

<script>
import Keyboard from './KeyboardLayout.vue';

export default {
  components: {
    Keyboard
  },
  data() {
    return {
      gameBoard: [
        [{ input: '', completed: false }, { input: '', completed: false }, { input: '', completed: false }, { input: '', completed: false }, { input: '', completed: false }],
        [{ input: '', completed: false }, { input: '', completed: false }, { input: '', completed: false }, { input: '', completed: false }, { input: '', completed: false }],
        [{ input: '', completed: false }, { input: '', completed: false }, { input: '', completed: false }, { input: '', completed: false }, { input: '', completed: false }],
        [{ input: '', completed: false }, { input: '', completed: false }, { input: '', completed: false }, { input: '', completed: false }, { input: '', completed: false }],
        [{ input: '', completed: false }, { input: '', completed: false }, { input: '', completed: false }, { input: '', completed: false }, { input: '', completed: false }]
      ],
      targetStrings: ['APPLE', 'BANANA', 'ORANGE', 'PEAR', 'KIWI'],
      activeRowIndex: 0, // Index of the currently active row
      activeColIndex: 0 // Index of the currently active column
    };
  },
  computed: {
    keyboardLayout() {
      // Generate an on-screen keyboard layout
      return [
        ['Q', 'W', 'E', 'R', 'T', 'Y', 'U', 'I', 'O', 'P'],
        ['A', 'S', 'D', 'F', 'G', 'H', 'J', 'K', 'L'],
        ['Z', 'X', 'C', 'V', 'B', 'N', 'M']
      ];
    }
  },
  methods: {
    appendToActiveRow(key) {
      // Append the clicked key to the input field of the active cell
      this.gameBoard[this.activeRowIndex][this.activeColIndex].input += key;
      // Move to the next column
      if (this.activeColIndex < this.gameBoard[0].length - 1) {
        this.activeColIndex++;
      } else {
        // Move to the next row if at the end of the current row
        this.activeRowIndex++;
        this.activeColIndex = 0;
      }
    },
    deleteLastCharacter() {
      // Find the index of the last filled column in the current row
      let lastFilledColIndex = -1;
      for (let i = this.gameBoard[this.activeRowIndex].length - 1; i >= 0; i--) {
        if (this.gameBoard[this.activeRowIndex][i].input !== '') {
          lastFilledColIndex = i;
          break;
        }
      }
      // Ensure that there's a filled column to delete from
      if (lastFilledColIndex !== -1) {
        // Get the input field of the last filled cell in the row and delete the last character
        const currentCell = this.gameBoard[this.activeRowIndex][lastFilledColIndex];
        if (currentCell.input) {
          currentCell.input = currentCell.input.slice(0, -1);
        }
        // Update active column index to point to the column of the cell just deleted from
        this.activeColIndex = lastFilledColIndex;
      }
    },
    checkRow(rowIndex) {
      const input = this.gameBoard[rowIndex].map(cell => cell.input).join('').toUpperCase();
      if (input === this.targetStrings[rowIndex]) {
        this.gameBoard[rowIndex].forEach(cell => cell.completed = true);
        alert('Row completed!');
      } else {
        alert('Incorrect input. Try again.');
      }
      // Reset active column index and move to the next row
      this.activeColIndex = 0;
      this.activeRowIndex++;
    }
  }
};
</script>

<style scoped>
.game-board {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.row {
  display: flex;
}

.cell {
  width: 30px;
  height: 30px;
  border: 1px solid #ccc;
}

.input-field {
  width: 100%;
  height: 100%;
  text-align: center;
  border: none;
  outline: none;
}

</style>
