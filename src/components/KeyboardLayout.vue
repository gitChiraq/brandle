<template>
  <div class="keyboard">
    <div class="keyboard-row">
      <div v-for="key in row1" :key="key" class="keyboard-key" @click="appendToActiveRow(key)">
        {{ key }}
      </div>
    </div>
    <div class="keyboard-row">
      <div v-for="key in row2" :key="key" class="keyboard-key" @click="appendToActiveRow(key)">
        {{ key }}
      </div>
    </div>
    <div class="keyboard-row">
      <div v-for="key in row3" :key="key" class="keyboard-key" @click="appendToActiveRow(key)">
        {{ key }}
      </div>
    </div>
    <div class="keyboard-row">
      <div class="keyboard-key" @click="deleteLastCharacter">DEL</div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    keyboardLayout: Array, // Keyboard layout array
    activeRowIndex: Number, // Active row index from parent component
    activeColIndex: Number // Active column index from parent component
  },
  computed: {
    row1() {
      return this.keyboardLayout[0];
    },
    row2() {
      return this.keyboardLayout[1];
    },
    row3() {
      return this.keyboardLayout[2];
    }
  },
  methods: {
    appendToActiveRow(key) {
      // Emit an event to the parent component to append the clicked key to the active row
      this.$emit('key-click', key);
    },
    deleteLastCharacter() {
      // Emit an event to the parent component to delete the last character
      this.$emit('delete-click');
    }
  }
};
</script>

<style scoped>
.keyboard {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.keyboard-row {
  display: flex;
}

.keyboard-key {
  background-color: #f0f0f0;
  border: 1px solid #ccc;
  text-align: center;
  cursor: pointer;
  padding: 10px;
  margin: 5px;
}

.keyboard-key:hover {
  background-color: #e0e0e0;
}
</style>
