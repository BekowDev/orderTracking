<script setup lang="ts">
import { ref } from 'vue'
import OrderForm from './components/OrderForm.vue'
import OrderList from './components/OrderList.vue'

interface Order {
  title: string
  address: string
  status: string
  id: number
}
const orders = ref<Order[]>([])

const addOrder = (order: Omit<Order, 'id'>) => {
  orders.value.push({ ...order, id: Date.now() })
}
</script>

<template>
  <div class="container">
    <h1 class="title">Управление заказами</h1>
    <OrderForm @add-order="addOrder" />
    <OrderList :orders="orders" class="order-list" />
  </div>
</template>
