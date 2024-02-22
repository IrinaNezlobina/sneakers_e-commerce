<template>
  <div class="fixed top-0 left-0 w-full h-full bg-black opacity-50"></div>
  <div class="bg-white w-96 h-full fixed right-0 top-0 z-20 p-8">
 <DrawerHead/>
 <CartItemList/>

 <div class="flex gap-4 mt-7 flex-col">
  <div class="flex gap-2">
    <span>
      Итого
      <div class="flex-1 border-b border-dashed"></div>
    </span>
    <b>1290</b>
  </div>
  <div class="flex gap-2">
    <span>
      Налог 5%
      <div class="flex-1 border-b border-dashed"></div>
    </span>
    <b>990</b>
  </div>
   <button disabled class="mt-4 cursor-pointer bg-lime-500 w-full text-white hover:bg-lime-600 transition active:bg-lime-700 disabled:bg-slate-300  rounded-xl py-3">
  Оформить
 </button>
 </div>

  </div>
</template>

<script setup>
import DrawerHead from './DrawerHead.vue'
import CartItemList from './CartItemList.vue';
</script>

<style scoped></style>
