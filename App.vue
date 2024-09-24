<template>
  <div class="shopping-list-app">
    <h1>Shopping List</h1>

    <div class="input-section">
      <input 
        v-model="newItem" 
        placeholder="Add a new item" 
        @keyup.enter="addItem" 
        class="input-field"
      />
      <button 
        :disabled="!newItem.trim()" 
        @click="addItem" 
        class="add-btn"
      >
        Add
      </button>
    </div>

    <ul class="item-list">
      <li 
        v-for="(item, index) in items" 
        :key="index" 
        class="item-entry"
      >
        <span>{{ item }}</span>
        <button @click="removeItem(index)" class="remove-btn">Remove</button>
      </li>
    </ul>

    <p v-if="items.length === 0" class="no-items">No items in the list. Start adding some!</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newItem: '',
      items: [],
    };
  },
  methods: {
    addItem() {
      if (this.newItem.trim()) {
        this.items.push(this.newItem);
        this.newItem = '';
      }
    },
    removeItem(index) {
      this.items.splice(index, 1);
    },
  },
};
</script>

<style scoped>
.shopping-list-app {
  max-width: 600px;
  margin: 50px auto;
  padding: 20px;
  background-color: #f0f8ff;
  border-radius: 12px;
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
  text-align: center;
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
}

h1 {
  color: #333;
  font-size: 2.5rem;
  margin-bottom: 20px;
}

.input-section {
  display: flex;
  justify-content: center;
  align-items: center;
  margin-bottom: 20px;
}

.input-field {
  width: 60%;
  padding: 10px;
  font-size: 1.2rem;
  border: 2px solid #ccc;
  border-radius: 8px;
  margin-right: 10px;
  outline: none;
}

.add-btn {
  padding: 10px 20px;
  font-size: 1.1rem;
  background-color: #28a745;
  color: white;
  border: none;
  border-radius: 8px;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

.add-btn:disabled {
  background-color: #c8e6c9;
  cursor: not-allowed;
}

.add-btn:not(:disabled):hover {
  background-color: #218838;
}

.item-list {
  list-style-type: none;
  padding: 0;
}

.item-entry {
  display: flex;
  justify-content: space-between;
  align-items: center;
  background-color: white;
  padding: 10px;
  margin-bottom: 10px;
  border-radius: 8px;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
}

.item-entry span {
  font-size: 1.2rem;
}

.remove-btn {
  background-color: #dc3545;
  color: white;
  border: none;
  padding: 6px 12px;
  border-radius: 6px;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

.remove-btn:hover {
  background-color: #c82333;
}

.no-items {
  font-size: 1.2rem;
  color: #777;
}
</style>
