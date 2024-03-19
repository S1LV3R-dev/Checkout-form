<script setup>
import { ref } from 'vue';
import cardInfo from './components/card_info.vue';
import orderInfo from './components/order_info.vue';
const price = ref(0);
const orders = ref([
    {
        id: 1,
        title: 'Title 1',
        description: 'Lorem, ipsum dolor',
        price: 150
    },
    {
        id: 2,
        title: 'Title 2',
        description: 'Lorem, ipsum dolor',
        price: 450
    },
    {
        id: 3,
        title: 'Title 3',
        description: 'Lorem, ipsum dolor',
        price: 500
    }
]);
for (let i = 0; i < orders.value.length; i++) {
    price.value += orders.value[i].price;
}
</script>

<template>
    <div id="checkout_form">
        <cardInfo :price="price"></cardInfo>
        <orderInfo :orders="orders"></orderInfo>
    </div>
</template>

<style scoped></style>
