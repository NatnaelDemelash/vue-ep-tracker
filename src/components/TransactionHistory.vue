<script setup>
import { defineProps } from 'vue';

const props = defineProps({
  transactions: {
    type: Array,
    required: true
  }
})

</script>


<template>
 <h3>History</h3>
  <ul class="list" id="list">
    <li v-for="item in transactions" :key="item.id" :class="item.amount < 0 ? 'minus' : 'plus'">
      {{ item.text }} <span>$ {{ item.amount }}</span>
    </li>
  </ul>
</template>


