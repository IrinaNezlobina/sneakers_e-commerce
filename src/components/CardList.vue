<template>
  <div class="grid grid-cols-4 gap-5">
    <Card
      v-for="item in items"
      :key="item.id"
      :on-click-add="onClickAdd"
      :is-favorite="true"
      :is-added="true"
      :price="item.price"
      :title="item.title"
      :image-url="item.imageUrl"
    />
    
  </div>
</template>

<script setup>
import Card from './Card.vue'
defineProps({
  items: Array
})
const onClickAdd = () => {
  alert(1)
}
</script>

<style scoped></style>
