<script setup>
import orderItem from './order_item.vue'
const props = defineProps({ orders: Array })
const orders = props.orders
</script>

<template>
  <div id="order_info_block">
    <h3>Order summary</h3>
    <div class="order-items">
      <div class="order-item" v-for="item in orders" :key="item.id">
        <orderItem>
          <template #title>
            {{ item.title }}
          </template>
          <template #description>
            {{ item.description }}
          </template>
          <template #price>
            {{ item.price }}
          </template>
        </orderItem>
      </div>
    </div>
  </div>
</template>
