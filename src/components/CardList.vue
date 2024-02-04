<template>
  <div class="grid grid-cols-4 gap-5">
    <Card
      :on-click-add="onClickAdd"
      :is-favorite="true"
      :is-added="true"
      :price="5000"
      title="Sneakers"
      image-url="/sneakers/sneakers-1.jpg"
    />
  </div>
</template>

<script setup>
import Card from './Card.vue'

const onClickAdd = () => {
  alert(1)
}
</script>

<style scoped></style>