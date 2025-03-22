<template>
  <form @submit.prevent="handleSubmit" class="form-container">
    <input v-model="title" placeholder="Название товара" required class="input-field" />
    <input v-model="address" placeholder="Адрес доставки" required class="input-field" />
    <select v-model="status" class="input-field">
      <option value="В обработке">В обработке</option>
      <option value="В пути">В пути</option>
      <option value="Доставлено">Доставлено</option>
    </select>
    <button type="submit" class="submit-button">Добавить заказ</button>
  </form>
</template>

<script setup lang="ts">
import { ref, defineEmits } from 'vue'

const title = ref('')
const address = ref('')
const status = ref('В обработке')
const emit = defineEmits(['add-order'])

const handleSubmit = () => {
  emit('add-order', { title: title.value, address: address.value, status: status.value })
  title.value = ''
  address.value = ''
  status.value = 'В обработке'
}
</script>
<style scoped>
.form-container {
  display: flex;
  flex-direction: column;
  gap: 16px;
  border: 1px solid #ccc;
  padding: 16px;
  border-radius: 8px;
}

.input-field {
  border: 1px solid #ccc;
  padding: 8px;
  border-radius: 4px;
}

.submit-button {
  background-color: #3b82f6;
  color: white;
  padding: 8px;
  width: 100%;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

.submit-button:hover {
  background-color: #2563eb;
}
</style>
