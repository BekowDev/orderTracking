<template>
  <div class="table-container">
    <table class="table">
      <thead>
        <tr>
          <th class="table-header">Название</th>
          <th class="table-header">Адрес</th>
          <th class="table-header">Статус</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="order in orders" :key="order.id" class="table-row">
          <td class="table-cell">{{ order.title }}</td>
          <td class="table-cell">{{ order.address }}</td>
          <td class="table-cell">{{ order.status }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script setup lang="ts">
import { defineProps } from 'vue'

interface Order {
  id: number
  title: string
  address: string
  status: string
}

defineProps<{ orders: Order[] }>()
</script>

<style scoped>
.table-container {
  border: 1px solid #ccc;
  padding: 16px;
  border-radius: 8px;
}

.table {
  width: 100%;
  border-collapse: collapse;
}

.table-header,
.table-cell {
  border: 1px solid #ccc;
  padding: 8px;
  text-align: left;
}

.table-header {
  background-color: #f3f4f6;
  font-weight: bold;
}

.table-row:nth-child(even) {
  background-color: #f9fafb;
}
</style>
