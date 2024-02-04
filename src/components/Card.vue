<template>
  <div class="">
    <div
      class="relative bg-white border border-slate-100 rounded-3xl p-8 cursor-pointer transition hover:-translate-y-2 hover:shadow-xl"
    >
      <img
        :src="!isFavorite ? '/like-1.svg' : '/like-2.svg'"
        class="absolute top-8 left-8"
        @click="onClickFavorite"
        alt=""
      />
      <img :src="imageUrl" alt="" />
      <p class="mt-2">{{ title }}</p>
      <div class="flex justify-between mt-5">
        <div class="flex flex-column">
          <span class="text-slate-400"> Цена</span>
          <b>{{ price }}</b>
        </div>
        <img @click="onClickAdd" :src="!isAdded ? '/plus.svg' : '/checked.svg'" alt="" />
      </div>
    </div>
  </div>
</template>

<script setup>
defineProps({
  imageUrl: String,
  title: String,
  price: Number,
  isFavorite: Boolean,
  isAdded: Boolean,
  onClickAdd: Function,
  onClickFavorite: Function
})
</script>

<style scoped></style>
